---
title: Použití překladače kontraktů dat
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: d9082d2979cf9bd0837635af567d69ef34c2e312
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975963"
---
# <a name="using-a-data-contract-resolver"></a>Použití překladače kontraktů dat
Překladač kontraktu dat umožňuje dynamicky konfigurovat známé typy. Známé typy jsou požadovány při serializaci nebo deserializaci typu, který není očekáván kontraktem dat. Další informace o známých typech najdete v tématu [známé typy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). Známé typy jsou obvykle určeny staticky. To znamená, že byste museli znát všechny možné typy, které může operace při implementaci operace obdržet. Existují scénáře, ve kterých není tato hodnota pravdivá a je možné dynamicky zadat známé typy, je důležité.  
  
## <a name="creating-a-data-contract-resolver"></a>Vytvoření překladače kontraktu dat  
 Vytvoření překladače kontraktu dat zahrnuje implementaci dvou metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>. Tyto dvě metody implementují zpětná volání, která se používají během serializace a deserializace v uvedeném pořadí. Metoda <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je vyvolána během serializace a přebírá typ kontraktu dat a mapuje je na `xsi:type` název a obor názvů. Metoda <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je vyvolána během deserializace a přebírá `xsi:type` název a obor názvů a překládá je na typ kontraktu dat. Obě tyto metody mají parametr `knownTypeResolver`, který lze použít k použití výchozího překladače známého typu v implementaci.  
  
 Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> pro mapování na a z typu kontraktu dat s názvem `Customer` odvozený z typu kontraktu dat `Person`.  
  
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
  
 Po definování <xref:System.Runtime.Serialization.DataContractResolver> můžete ji použít předáním do konstruktoru <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu.  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> ve volání metod <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 Můžete ji také nastavit na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>, jak je znázorněno v následujícím příkladu.  
  
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
  
 Překladač kontraktu dat lze deklarativně zadat implementací atributu, který lze použít na službu.  Další informace najdete v ukázce [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) . Tato ukázka implementuje atribut nazvaný "KnownAssembly", který do chování služby přidá vlastní překladač kontraktu dat.  
  
## <a name="see-also"></a>Viz také:

- [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Ukázka DataContractSerializer](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
