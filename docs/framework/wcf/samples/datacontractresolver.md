---
title: DataContractResolver
ms.date: 03/30/2017
ms.assetid: 6c200c02-bc14-4b8d-bbab-9da31185b805
ms.openlocfilehash: ad5436a60b5cd82b44931713d863eaeed791e264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723976"
---
# <a name="datacontractresolver"></a><span data-ttu-id="248da-102">DataContractResolver</span><span class="sxs-lookup"><span data-stu-id="248da-102">DataContractResolver</span></span>
<span data-ttu-id="248da-103">Tato ukázka předvádí, jak lze přizpůsobit procesů serializace a deserializace pomocí <xref:System.Runtime.Serialization.DataContractResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="248da-103">This sample demonstrates how the serialization and deserialization processes can be customized by using the <xref:System.Runtime.Serialization.DataContractResolver> class.</span></span> <span data-ttu-id="248da-104">Tento příklad ukazuje způsob použití modulu DataContractResolver Mapovat typy CLR do a z reprezentaci xsi: type během serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="248da-104">This sample shows how to use a DataContractResolver to map CLR types to and from an xsi:type representation during serialization and deserialization.</span></span>

## <a name="sample-details"></a><span data-ttu-id="248da-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="248da-105">Sample Details</span></span>
 <span data-ttu-id="248da-106">Ukázka definuje následující typy CLR.</span><span class="sxs-lookup"><span data-stu-id="248da-106">The sample defines the following CLR types.</span></span>

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

 <span data-ttu-id="248da-107">Ukázka načte sestavení, extrahuje každý z těchto typů a poté serializuje a deserializuje je.</span><span class="sxs-lookup"><span data-stu-id="248da-107">The sample loads the assembly, extracts each of these types, and then serializes and deserializes them.</span></span> <span data-ttu-id="248da-108"><xref:System.Runtime.Serialization.DataContractResolver> Zapojí se do procesu serializace předáním instance <xref:System.Runtime.Serialization.DataContractResolver>-odvozené třídy <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="248da-108">The <xref:System.Runtime.Serialization.DataContractResolver> is plugged into the serialization process by passing an instance of the <xref:System.Runtime.Serialization.DataContractResolver>-derived class to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, as shown in the following example.</span></span>

```csharp
this.serializer = new DataContractSerializer(typeof(Object), null, int.MaxValue, false, true, null, new MyDataContractResolver(assembly));
```

 <span data-ttu-id="248da-109">Ukázka pak Serializuje typy CLR, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="248da-109">The sample then serializes the CLR types as shown in the following code example.</span></span>

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

 <span data-ttu-id="248da-110">Ukázka pak deserializuje xsi:types, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="248da-110">The sample then deserializes the xsi:types as shown in the following code example.</span></span>

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

 <span data-ttu-id="248da-111">Od vlastní <xref:System.Runtime.Serialization.DataContractResolver> je předán <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> je volaný během serializace pro mapování typu CLR na ekvivalentní `xsi:type`.</span><span class="sxs-lookup"><span data-stu-id="248da-111">Since the custom <xref:System.Runtime.Serialization.DataContractResolver> is passed in to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor, the <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> is called during serialization to map a CLR type to an equivalent `xsi:type`.</span></span> <span data-ttu-id="248da-112">Podobně jako <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> je volán během deserializaci k mapování `xsi:type` na ekvivalentní typ CLR.</span><span class="sxs-lookup"><span data-stu-id="248da-112">Similarly the <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> is called during deserialization to map the `xsi:type` to an equivalent CLR type.</span></span> <span data-ttu-id="248da-113">V této ukázce <xref:System.Runtime.Serialization.DataContractResolver> je definován, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="248da-113">In this sample, the <xref:System.Runtime.Serialization.DataContractResolver> is defined as shown in the following example.</span></span>

 <span data-ttu-id="248da-114">Následující příklad kódu je třídu odvozenou z <xref:System.Runtime.Serialization.DataContractResolver>.</span><span class="sxs-lookup"><span data-stu-id="248da-114">The following code example is a class deriving from <xref:System.Runtime.Serialization.DataContractResolver>.</span></span>

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

 <span data-ttu-id="248da-115">Jako součást vzorku generuje typy projektu sestavení se všemi typy, které se používají v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="248da-115">As part of the sample, the Types project generates the assembly with all the types that are used in this sample.</span></span> <span data-ttu-id="248da-116">Pomocí tohoto projektu můžete přidat, odebrat nebo změnit typy, které bude serializována.</span><span class="sxs-lookup"><span data-stu-id="248da-116">Use this project to add, remove or modify the types that will be serialized.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="248da-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="248da-117">To use this sample</span></span>

1.  <span data-ttu-id="248da-118">Pomocí sady Visual Studio 2012, otevřete soubor řešení DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="248da-118">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2.  <span data-ttu-id="248da-119">Abyste mohli spustit řešení, stisknutím klávesy F5</span><span class="sxs-lookup"><span data-stu-id="248da-119">To run the solution, press F5</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="248da-120">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="248da-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="248da-121">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="248da-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="248da-122">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="248da-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="248da-123">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="248da-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractResolver`  
  
## <a name="see-also"></a><span data-ttu-id="248da-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="248da-124">See also</span></span>
- [<span data-ttu-id="248da-125">Použití překladače kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="248da-125">Using a Data Contract Resolver</span></span>](../../../../docs/framework/wcf/feature-details/using-a-data-contract-resolver.md)
