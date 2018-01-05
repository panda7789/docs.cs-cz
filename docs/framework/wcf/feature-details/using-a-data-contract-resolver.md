---
title: "Použití překladače kontraktů dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28bba68c985191b69fea3b7ab85812917a827b30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="326af-102">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="326af-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="326af-103">Překladače kontraktů dat umožňuje nakonfigurovat známé typy dynamicky.</span><span class="sxs-lookup"><span data-stu-id="326af-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="326af-104">Známé typy jsou potřeba při serializaci nebo deserializaci typu kontraktu dat není očekávaný.</span><span class="sxs-lookup"><span data-stu-id="326af-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="326af-105">známé typy, najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="326af-105"> known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="326af-106">Známé typy jsou obvykle zadat staticky.</span><span class="sxs-lookup"><span data-stu-id="326af-106">Known types are normally specified statically.</span></span> <span data-ttu-id="326af-107">To znamená, budete muset znát možné typy operace se může zobrazit při provádění operace.</span><span class="sxs-lookup"><span data-stu-id="326af-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="326af-108">Existují scénáře, ve kterých to není PRAVDA a schopnost určit známé typy dynamicky je důležité.</span><span class="sxs-lookup"><span data-stu-id="326af-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="326af-109">Vytváření překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="326af-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="326af-110">Vytvoření překladače kontraktů dat zahrnuje implementace dvě metody, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="326af-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="326af-111">Tyto dvě metody implementovat zpětná volání, které se používají během serializace a deserializace, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="326af-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="326af-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> Metoda je volána během serializace a trvá typ kontraktu dat a mapuje jej do `xsi:type` názvem a oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="326af-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="326af-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> Metoda je volána při deserializaci a trvá `xsi:type` názvem a oborem názvů a přeloží na datový typ kontrakt.</span><span class="sxs-lookup"><span data-stu-id="326af-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="326af-114">Mají obě tyto metody `knownTypeResolver` parametr, který je možné použít výchozí překladač typu v implementaci známé.</span><span class="sxs-lookup"><span data-stu-id="326af-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="326af-115">Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> mapovat do a z typu kontraktu dat s názvem `Customer` odvozen od typu kontraktu dat `Person`.</span><span class="sxs-lookup"><span data-stu-id="326af-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="326af-116">Jakmile definujete <xref:System.Runtime.Serialization.DataContractResolver> předáním jeho můžete ji použít <xref:System.Runtime.Serialization.DataContractSerializer> konstruktor, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="326af-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```  
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="326af-117">Můžete zadat <xref:System.Runtime.Serialization.DataContractSerializer> v volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> metod, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="326af-117">You can specify a <xref:System.Runtime.Serialization.DataContractSerializer> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A> methods, as shown in the following example.</span></span>  
  
```  
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="326af-118">Nebo můžete nastavit na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="326af-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="326af-119">Překladače kontraktů dat deklarativně zadáte implementace atribut, který můžete použít ke službě.</span><span class="sxs-lookup"><span data-stu-id="326af-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="326af-120">[KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="326af-120"> the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="326af-121">Tato ukázka implementuje atribut nazvaný "KnownAssembly" doplňuje překladače kontraktů dat vlastní chování služby.</span><span class="sxs-lookup"><span data-stu-id="326af-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="326af-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="326af-122">See Also</span></span>  
 [<span data-ttu-id="326af-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="326af-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="326af-124">Ukázka DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="326af-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)  
 [<span data-ttu-id="326af-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="326af-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
