---
title: Použití překladače kontraktů dat
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: b1c545d84db68f4b13925dd9088cc9d81050b5e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222442"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="7c7d0-102">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7c7d0-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="7c7d0-103">Překladače kontraktů dat umožňuje dynamicky konfigurovat známých typů.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="7c7d0-104">Známé typy jsou potřeba při serializaci nebo deserializaci typ není očekávaný datový kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="7c7d0-105">Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7c7d0-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="7c7d0-106">Známé typy jsou obvykle určeny staticky.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-106">Known types are normally specified statically.</span></span> <span data-ttu-id="7c7d0-107">To znamená, že budete muset zjistit všechny možné typy, operace se může zobrazit při provádění operace.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="7c7d0-108">Existují scénáře, ve kterých to neplatí a schopnost dynamicky určit známých typů není důležité.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="7c7d0-109">Vytváření překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7c7d0-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="7c7d0-110">Vytvoření překladače kontraktů dat zahrnuje implementaci dvou metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="7c7d0-111">Tyto dvě metody implementovat zpětná volání, které se používají během serializace a deserializace, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="7c7d0-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda je vyvolána během serializace a přijímá typ kontraktu dat a mapuje na `xsi:type` názvem a oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="7c7d0-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda je vyvolána během deserializace za a má `xsi:type` názvem a oborem názvů a přeloží je pro typ kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="7c7d0-114">Obě tyto metody mají `knownTypeResolver` parametr, který je možné použít výchozí překladač typů ve vaší implementaci známé.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="7c7d0-115">Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> mapovat do a z typ kontraktu dat s názvem `Customer` odvozen od typu kontraktu dat `Person`.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="7c7d0-116">Po definování <xref:System.Runtime.Serialization.DataContractResolver> slouží ji do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="7c7d0-117">Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> ve volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="7c7d0-118">Nebo můžete nastavit na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="7c7d0-119">Překladače kontraktů dat deklarativně zadáte implementace atribut, který lze použít ke službě.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="7c7d0-120">Další informace najdete v tématu [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="7c7d0-121">Tato ukázka implementuje atribut s názvem "KnownAssembly", který přidá překladače kontraktů dat vlastní chování služby.</span><span class="sxs-lookup"><span data-stu-id="7c7d0-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7d0-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c7d0-122">See also</span></span>

- [<span data-ttu-id="7c7d0-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="7c7d0-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="7c7d0-124">Ukázka DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="7c7d0-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="7c7d0-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="7c7d0-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
