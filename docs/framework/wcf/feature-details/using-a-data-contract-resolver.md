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
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="94e22-102">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="94e22-102">Using a Data Contract Resolver</span></span>
<span data-ttu-id="94e22-103">Překladač kontraktu dat umožňuje dynamicky konfigurovat známé typy.</span><span class="sxs-lookup"><span data-stu-id="94e22-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="94e22-104">Známé typy jsou požadovány při serializaci nebo deserializaci typu, který není očekáván kontraktem dat.</span><span class="sxs-lookup"><span data-stu-id="94e22-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="94e22-105">Další informace o známých typech najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="94e22-105">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="94e22-106">Známé typy jsou obvykle určeny staticky.</span><span class="sxs-lookup"><span data-stu-id="94e22-106">Known types are normally specified statically.</span></span> <span data-ttu-id="94e22-107">To znamená, že byste museli znát všechny možné typy, které může operace při implementaci operace obdržet.</span><span class="sxs-lookup"><span data-stu-id="94e22-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="94e22-108">Existují scénáře, ve kterých není tato hodnota pravdivá a je možné dynamicky zadat známé typy, je důležité.</span><span class="sxs-lookup"><span data-stu-id="94e22-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="94e22-109">Vytvoření překladače kontraktu dat</span><span class="sxs-lookup"><span data-stu-id="94e22-109">Creating a Data Contract Resolver</span></span>  
 <span data-ttu-id="94e22-110">Vytvoření překladače kontraktu dat zahrnuje implementaci dvou metod, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> a <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> .</span><span class="sxs-lookup"><span data-stu-id="94e22-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="94e22-111">Tyto dvě metody implementují zpětná volání, která se používají během serializace a deserializace v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="94e22-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="94e22-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A>Metoda je vyvolána během serializace a přebírá typ kontraktu dat a mapuje jej na `xsi:type` název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="94e22-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="94e22-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>Metoda je vyvolána během deserializace a přebírá `xsi:type` název a obor názvů a překládá je na typ kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="94e22-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="94e22-114">Obě tyto metody mají `knownTypeResolver` parametr, který lze použít k použití výchozího překladače známého typu v implementaci.</span><span class="sxs-lookup"><span data-stu-id="94e22-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="94e22-115">Následující příklad ukazuje, jak implementovat metodu <xref:System.Runtime.Serialization.DataContractResolver> pro mapování na typ kontraktu dat s názvem `Customer` odvozený z typu kontraktu dat a z něj `Person` .</span><span class="sxs-lookup"><span data-stu-id="94e22-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
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
  
 <span data-ttu-id="94e22-116">Po definování můžete <xref:System.Runtime.Serialization.DataContractResolver> jej použít předáním do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="94e22-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="94e22-117">Můžete zadat <xref:System.Runtime.Serialization.DataContractResolver> volání <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> metody nebo, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="94e22-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="94e22-118">Nebo ho můžete nastavit na, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="94e22-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="94e22-119">Překladač kontraktu dat lze deklarativně zadat implementací atributu, který lze použít na službu.</span><span class="sxs-lookup"><span data-stu-id="94e22-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="94e22-120">Další informace najdete v ukázce [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) .</span><span class="sxs-lookup"><span data-stu-id="94e22-120">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="94e22-121">Tato ukázka implementuje atribut nazvaný "KnownAssembly", který do chování služby přidá vlastní překladač kontraktu dat.</span><span class="sxs-lookup"><span data-stu-id="94e22-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e22-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="94e22-122">See also</span></span>

- [<span data-ttu-id="94e22-123">Známé typy kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="94e22-123">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="94e22-124">Ukázka třídy DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="94e22-124">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="94e22-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="94e22-125">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
