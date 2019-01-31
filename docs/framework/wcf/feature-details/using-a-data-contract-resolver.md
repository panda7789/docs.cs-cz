---
title: Použití překladače kontraktů dat
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: 844c4e0861c2cf4e6acb2b128ff1f5cefa0f7fa0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279146"
---
# <a name="using-a-data-contract-resolver"></a>Použití překladače kontraktů dat
Překladače kontraktů dat umožňuje dynamicky konfigurovat známých typů. Známé typy jsou potřeba při serializaci nebo deserializaci typ není očekávaný datový kontrakt. Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Známé typy jsou obvykle určeny staticky. To znamená, že budete muset zjistit všechny možné typy, operace se může zobrazit při provádění operace. Existují scénáře, ve kterých to neplatí a schopnost dynamicky určit známých typů není důležité.  
  
## <a name="creating-a-data-contract-resolver"></a>Vytváření překladače kontraktů dat  
 Vytvoření překladače kontraktů dat zahrnuje implementaci dvou metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Tyto dvě metody implementovat zpětná volání, které se používají během serializace a deserializace, v uvedeném pořadí. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda je vyvolána během serializace a přijímá typ kontraktu dat a mapuje na `xsi:type` názvem a oborem názvů. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda je vyvolána během deserializace za a má `xsi:type` názvem a oborem názvů a přeloží je pro typ kontraktu dat. Obě tyto metody mají `knownTypeResolver` parametr, který je možné použít výchozí překladač typů ve vaší implementaci známé.  
  
 Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> mapovat do a z typ kontraktu dat s názvem `Customer` odvozen od typu kontraktu dat `Person`.  
  
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
  
 Po definování <xref:System.Runtime.Serialization.DataContractResolver> slouží ji do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> ve volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metod, jak je znázorněno v následujícím příkladu.  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Nebo můžete nastavit na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak je znázorněno v následujícím příkladu.  
  
```  
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
  
 Překladače kontraktů dat deklarativně zadáte implementace atribut, který lze použít ke službě.  Další informace najdete v tématu [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) vzorku. Tato ukázka implementuje atribut s názvem "KnownAssembly", který přidá překladače kontraktů dat vlastní chování služby.  
  
## <a name="see-also"></a>Viz také:
- [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Ukázka DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
