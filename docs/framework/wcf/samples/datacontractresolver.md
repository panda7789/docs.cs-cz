---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: 716bcb2bb43656051beffb15da9c7a988942ecd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183787"
---
# <a name="datacontractresolver"></a><span data-ttu-id="411a5-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="411a5-102">DataContractResolver</span></span>
<span data-ttu-id="411a5-103">Tato ukázka ukazuje, jak serializace a deserializace procesy lze přizpůsobit pomocí třídy. <xref:System.Runtime.Serialization.DataContractResolver></span><span class="sxs-lookup"><span data-stu-id="411a5-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="411a5-104">Tato ukázka ukazuje, jak pomocí DataContractResolver mapovat typy CLR do a z xsi:typ reprezentace během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="411a5-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="411a5-105">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="411a5-105">Sample Details</span></span>
 <span data-ttu-id="411a5-106">Ukázka definuje následující typy CLR.</span><span class="sxs-lookup"><span data-stu-id="411a5-106">The sample defines the following CLR types.</span></span>

```csharp
using System;
using System.Runtime.Serialization;

namespace Types
{
    [DataContract]
    public class Customer
    {
        [DataMember]
        public string Name { get; set; }
    }

    [DataContract]
    public class VIPCustomer : Customer
    {
        [DataMember]
        public string VipInfo { get; set; }
    }

    [DataContract]
    public class RegularCustomer : Customer
    {
    }

    [DataContract]
    public class PreferredVIPCustomer : VIPCustomer
    {
    }
}
```

 <span data-ttu-id="411a5-107">Ukázka načte sestavu, extrahuje každý z těchto typů a potom je serializuje a reserializuje.</span><span class="sxs-lookup"><span data-stu-id="411a5-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="411a5-108">Je <xref:System.Runtime.Serialization.DataContractResolver> zapojen do procesu serializace předáním <xref:System.Runtime.Serialization.DataContractResolver>instance -derived <xref:System.Runtime.Serialization.DataContractSerializer> třídy konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="411a5-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="411a5-109">Ukázka pak serializuje typy CLR, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="411a5-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

```csharp
Assembly assembly = Assembly.Load(new AssemblyName("Types"));

public void serialize(Type type)
{
    Object instance = Activator.CreateInstance(type);

    Console.WriteLine("----------------------------------------");
    Console.WriteLine();
    Console.WriteLine("Serializing type: {0}", type.Name);
    Console.WriteLine();
    this.buffer = new StringBuilder();
    using (XmlWriter xmlWriter = XmlWriter.Create(this.buffer))
    {
        try
        {
            this.serializer.WriteObject(xmlWriter, instance);
        }
        catch (SerializationException error)
        {
            Console.WriteLine(error.ToString());
        }
    }
    Console.WriteLine(this.buffer.ToString());
}
```

 <span data-ttu-id="411a5-110">Ukázka pak deserializuje xsi:typy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="411a5-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

```csharp
public void deserialize(Type type)
{
    Console.WriteLine();
    Console.WriteLine("Deserializing type: {0}", type.Name);
    Console.WriteLine();
    using (XmlReader xmlReader = XmlReader.Create(new StringReader(this.buffer.ToString())))
    {
        Object obj = this.serializer.ReadObject(xmlReader);
    }
}
```

 <span data-ttu-id="411a5-111">Vzhledem <xref:System.Runtime.Serialization.DataContractResolver> k tomu, <xref:System.Runtime.Serialization.DataContractSerializer> že vlastní <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je předán konstruktoru, je volána `xsi:type`během serializace mapovat typ CLR na ekvivalentní .</span><span class="sxs-lookup"><span data-stu-id="411a5-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="411a5-112">Podobně <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je volána během deserializace `xsi:type` mapovat na ekvivalentní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="411a5-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="411a5-113">V této ukázce <xref:System.Runtime.Serialization.DataContractResolver> je definována, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="411a5-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="411a5-114">Následující příklad kódu je třída odvozená <xref:System.Runtime.Serialization.DataContractResolver>z .</span><span class="sxs-lookup"><span data-stu-id="411a5-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private Dictionary<string, XmlDictionaryString> dictionary = new Dictionary<string, XmlDictionaryString>();
    Assembly assembly;

    public MyDataContractResolver(Assembly assembly)
    {
        this.assembly = assembly;
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        XmlDictionaryString tName;
        XmlDictionaryString tNamespace;
        if (dictionary.TryGetValue(typeName, out tName) && dictionary.TryGetValue(typeNamespace, out tNamespace))
        {
            return this.assembly.GetType(tNamespace.Value + "." + tName.Value);
        }
        else
        {
            return null;
        }
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        string name = dataContractType.Name;
        string namesp = dataContractType.Namespace;
        typeName = new XmlDictionaryString(XmlDictionary.Empty, name, 0);
        typeNamespace = new XmlDictionaryString(XmlDictionary.Empty, namesp, 0);
        if (!dictionary.ContainsKey(dataContractType.Name))
        {
            dictionary.Add(name, typeName);
        }
        if (!dictionary.ContainsKey(dataContractType.Namespace))
        {
            dictionary.Add(namesp, typeNamespace);
        }
    }
}
```

 <span data-ttu-id="411a5-115">Jako součást vzorku Typy projektu generuje sestavení se všemi typy, které se používají v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="411a5-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="411a5-116">Tento projekt slouží k přidání, odebrání nebo úpravě typů, které budou serializovány.</span><span class="sxs-lookup"><span data-stu-id="411a5-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="411a5-117">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="411a5-117">To use this sample</span></span>

1. <span data-ttu-id="411a5-118">Pomocí Visual Studia 2012 otevřete soubor řešení DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="411a5-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="411a5-119">Chcete-li řešení spustit, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="411a5-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
> <span data-ttu-id="411a5-120">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="411a5-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="411a5-121">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="411a5-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="411a5-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="411a5-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="411a5-123">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="411a5-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="411a5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="411a5-124">See also</span></span>

- [<span data-ttu-id="411a5-125">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="411a5-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
