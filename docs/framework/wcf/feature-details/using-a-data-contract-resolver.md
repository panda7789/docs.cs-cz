---
title: Použití překladače kontraktů dat
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 20abd4d928fc51eb359949ecbb216615e9659b7f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595021"
---
# <a name="using-a-data-contract-resolver"></a>Použití překladače kontraktů dat
Překladač kontraktu dat umožňuje dynamicky konfigurovat známé typy. Známé typy jsou požadovány při serializaci nebo deserializaci typu, který není očekáván kontraktem dat. Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md). Známé typy jsou obvykle určeny staticky. To znamená, že byste museli znát všechny možné typy, které může operace při implementaci operace obdržet. Existují scénáře, ve kterých není tato hodnota pravdivá a je možné dynamicky zadat známé typy, je důležité.  
  
## <a name="creating-a-data-contract-resolver"></a>Vytvoření překladače kontraktu dat  
 Vytvoření překladače kontraktu dat zahrnuje implementaci dvou metod, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> . Tyto dvě metody implementují zpětná volání, která se používají během serializace a deserializace v uvedeném pořadí. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>Metoda je vyvolána během serializace a přebírá typ kontraktu dat a mapuje jej na `xsi:type` název a obor názvů. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>Metoda je vyvolána během deserializace a přebírá `xsi:type` název a obor názvů a překládá je na typ kontraktu dat. Obě tyto metody mají `knownTypeResolver` parametr, který lze použít k použití výchozího překladače známého typu v implementaci.  
  
 Následující příklad ukazuje, jak implementovat metodu <xref:System.Runtime.Serialization.DataContractResolver> pro mapování na typ kontraktu dat s názvem `Customer` odvozený z typu kontraktu dat a z něj `Person` .  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 Po definování můžete <xref:System.Runtime.Serialization.DataContractResolver> jej použít předáním do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metody nebo, jak je znázorněno v následujícím příkladu.  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Nebo ho můžete nastavit na, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak je znázorněno v následujícím příkladu.  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 Překladač kontraktu dat lze deklarativně zadat implementací atributu, který lze použít na službu.  Další informace najdete v ukázce [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) . Tato ukázka implementuje atribut nazvaný "KnownAssembly", který do chování služby přidá vlastní překladač kontraktu dat.  
  
## <a name="see-also"></a>Viz také

- [Známé typy kontraktů dat](data-contract-known-types.md)
- [Ukázka třídy DataContractSerializer](../samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../samples/knownassemblyattribute.md)
