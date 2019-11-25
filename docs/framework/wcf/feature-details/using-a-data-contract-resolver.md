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
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="32321-102">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="32321-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="32321-103">Překladač kontraktu dat umožňuje dynamicky konfigurovat známé typy.</span><span class="sxs-lookup"><span data-stu-id="32321-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="32321-104">Známé typy jsou požadovány při serializaci nebo deserializaci typu, který není očekáván kontraktem dat.</span><span class="sxs-lookup"><span data-stu-id="32321-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="32321-105">Další informace o známých typech najdete v tématu [známé typy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="32321-105">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="32321-106">Známé typy jsou obvykle určeny staticky.</span><span class="sxs-lookup"><span data-stu-id="32321-106">Known types are normally specified statically.</span></span> <span data-ttu-id="32321-107">To znamená, že byste museli znát všechny možné typy, které může operace při implementaci operace obdržet.</span><span class="sxs-lookup"><span data-stu-id="32321-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="32321-108">Existují scénáře, ve kterých není tato hodnota pravdivá a je možné dynamicky zadat známé typy, je důležité.</span><span class="sxs-lookup"><span data-stu-id="32321-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="32321-109">Vytvoření překladače kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="32321-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="32321-110">Vytvoření překladače kontraktu dat zahrnuje implementaci dvou metod <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span><span class="sxs-lookup"><span data-stu-id="32321-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="32321-111">Tyto dvě metody implementují zpětná volání, která se používají během serializace a deserializace v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="32321-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="32321-112">Metoda <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je vyvolána během serializace a přebírá typ kontraktu dat a mapuje je na `xsi:type` název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="32321-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="32321-113">Metoda <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je vyvolána během deserializace a přebírá `xsi:type` název a obor názvů a překládá je na typ kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="32321-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="32321-114">Obě tyto metody mají parametr `knownTypeResolver`, který lze použít k použití výchozího překladače známého typu v implementaci.</span><span class="sxs-lookup"><span data-stu-id="32321-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="32321-115">Následující příklad ukazuje, jak implementovat <xref:System.Runtime.Serialization.DataContractResolver> pro mapování na a z typu kontraktu dat s názvem `Customer` odvozený z typu kontraktu dat `Person`.</span><span class="sxs-lookup"><span data-stu-id="32321-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="32321-116">Po definování <xref:System.Runtime.Serialization.DataContractResolver> můžete ji použít předáním do konstruktoru <xref:System.Runtime.Serialization.DataContractSerializer>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32321-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="32321-117">Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> ve volání metod <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> nebo <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32321-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="32321-118">Můžete ji také nastavit na <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="32321-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="32321-119">Překladač kontraktu dat lze deklarativně zadat implementací atributu, který lze použít na službu.</span><span class="sxs-lookup"><span data-stu-id="32321-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="32321-120">Další informace najdete v ukázce [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="32321-120">For more information, see the [KnownAssemblyAttribute](../../../../docs/framework/wcf/samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="32321-121">Tato ukázka implementuje atribut nazvaný "KnownAssembly", který do chování služby přidá vlastní překladač kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="32321-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32321-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32321-122">See also</span></span>

- [<span data-ttu-id="32321-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="32321-123">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="32321-124">Ukázka DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="32321-124">DataContractSerializer Sample</span></span>](../../../../docs/framework/wcf/samples/datacontractserializer-sample.md)
- [<span data-ttu-id="32321-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="32321-125">KnownAssemblyAttribute</span></span>](../../../../docs/framework/wcf/samples/knownassemblyattribute.md)
