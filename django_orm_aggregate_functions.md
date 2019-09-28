# This is related to aggrigation function


>>> from api.vehicles.models import Vehicles
>>> Vehicles.objects.all()
<QuerySet [<Vehicles: D_190914T110128_0_0000376013_035>, <Vehicles: D_190914T110128_0_0000375755_035>, <Vehicles: D_190914T110128_0_0000375874_035>, <Vehicles: D_190914T110128_0_0000376082_035>, <Vehicles: D_190914T110144_0_0000625648_035>, <Vehicles: D_190914T110146_0_0000168596_035>, <Vehicles: D_190914T110148_0_0000148103_035>, <Vehicles: D_190914T110150_0_0000725617_035>, <Vehicles: D_190914T110202_0_0000261711_035>, <Vehicles: D_190914T110207_0_0000434917_035>, <Vehicles: D_190922T070118_0_0000279910_035>, <Vehicles: D_190922T070118_0_0000279420_035>, <Vehicles: D_190922T070118_0_0000279217_035>, <Vehicles: D_190922T070118_0_0000279307_035>, <Vehicles: D_190922T070133_0_0000238969_035>, <Vehicles: D_190922T070133_0_0000994021_035>, <Vehicles: D_190922T070134_0_0000814236_035>, <Vehicles: D_190922T070135_0_0000768848_035>, <Vehicles: D_190922T070147_0_0000060697_035>, <Vehicles: D_190922T070148_0_0000600785_035>, '...(remaining elements truncated)...']>

##importing aggregate function
>>> from django.db.models import Sum,Avg,Min,Max

#Applyng Sum function
>>> Vehicles.objects.aggregate(Sum('size'))
{'size__sum': 1719901273}

#Applyng Avg function
>>> Vehicles.objects.aggregate(Avg('size'))
{'size__avg': 15635466.11818182}


#Assigning Avg value to  a named key
>>> Vehicles.objects.aggregate(avg_size=Avg('size'))
{'avg_size': 15635466.11818182}


#Assigning Avg value to a named key in a named dict
>>> result = Vehicles.objects.aggregate(avg_size=Avg('size'))
>>> result['avg_size']
15635466.11818182

#Assigning Avg & Sum value to to a named dict
>>> result = Vehicles.objects.aggregate(Avg('size'), Min('size'))
>>> result
{'size__avg': 15635466.11818182, 'size__min': 14873778}

#Assigning Avg & Sum value to a named dict with names keys
>>> result = Vehicles.objects.aggregate(avg_size=Avg('size'),min_size = Min('size'))
>>> result
{'avg_size': 15635466.11818182, 'min_size': 14873778}


