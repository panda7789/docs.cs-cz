---
title: Použití překladače kontraktů dat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53459517591c36430b9326d6605c4eb1b28a13e7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="using-a-data-contract-resolver"></a>Použití překladače kontraktů dat
Překladače kontraktů dat umožňuje nakonfigurovat známé typy dynamicky. Známé typy jsou potřeba při serializaci nebo deserializaci typu kontraktu dat není očekávaný. Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Známé typy jsou obvykle zadat staticky. To znamená, budete muset znát možné typy operace se může zobrazit při provádění operace. Existují scénáře, ve kterých to není PRAVDA a schopnost určit známé typy dynamicky je důležité.  
  
## <a name="creating-a-data-contract-resolver"></a>Vytváření překladače kontraktů dat  
 Vytvoření překladače kontraktů dat zahrnuje implementace dvě metody, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Tyto dvě metody implementovat zpětná volání, které se používají během serializace a deserializace, v uvedeném pořadí. <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda je volána během serializace a trvá typ kontraktu dat a mapuje jej do `xsi:type` názvem a oborem názvů. <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda je volána při deserializaci a trvá `xsi:type` názvem a oborem názvů a přeloží na datový typ kontrakt. Mají obě tyto metody `knownTypeResolver` parametr, který je možné použít výchozí překladač typu v implementaci známé.  
  
 Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> mapovat do a z typu kontraktu dat s názvem `Customer` odvozen od typu kontraktu dat `Person`.  
  
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
  
 Jakmile definujete <xref:System.Runtime.Serialization.DataContractResolver> předáním jeho můžete ji použít <xref:System.Runtime.Serialization.DataContractSerializer> konstruktor, jak je znázorněno v následujícím příkladu.  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Můžete zadat <xref:System.Runtime.Serialization.DataContractSerializer> v volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> metod, jak je znázorněno v následujícím příkladu.  
  
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
  
 Překladače kontraktů dat deklarativně zadáte implementace atribut, který můžete použít ke službě.  Další informace najdete v tématu [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) ukázka. Tato ukázka implementuje atribut nazvaný "KnownAssembly" doplňuje překladače kontraktů dat vlastní chování služby.  
  
## <a name="see-also"></a>Viz také  
 [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Ukázka DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
