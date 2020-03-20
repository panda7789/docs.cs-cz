---
title: Ukázka dataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144627"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="f96c9-102">Ukázka dataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="f96c9-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="f96c9-103">Tento vzorek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>je pro .</span><span class="sxs-lookup"><span data-stu-id="f96c9-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="f96c9-104">Pro většinu scénářů, které zahrnují serializaci a rekonstrukci json, doporučujeme api v [oboru názvů System.Text.Json](../../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f96c9-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="f96c9-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>podporuje stejné typy <xref:System.Runtime.Serialization.DataContractSerializer>jako .</span><span class="sxs-lookup"><span data-stu-id="f96c9-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="f96c9-106">Formát dat JSON je zvláště užitečný při psaní webových aplikací ve stylu JavaScriptu a XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="f96c9-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="f96c9-107">Podpora AJAX v systému Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="f96c9-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="f96c9-108">Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX, naleznete [v ajax ukázky](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="f96c9-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="f96c9-109">Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f96c9-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="f96c9-110">Ukázka používá `Person` kontrakt dat k předvedení serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="f96c9-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="f96c9-111">Chcete-li serializovat instanci `Person` typu do JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použijte metodu `WriteObject` k zápisu dat JSON do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="f96c9-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="f96c9-112">Datový proud paměti obsahuje platná data JSON.</span><span class="sxs-lookup"><span data-stu-id="f96c9-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="f96c9-113">Ukázka ukazuje deserializaci z dat JSON do objektu.</span><span class="sxs-lookup"><span data-stu-id="f96c9-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="f96c9-114">Potom přetoč proud `ReadObject`a volání .</span><span class="sxs-lookup"><span data-stu-id="f96c9-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="f96c9-115">Zkoumání objektu `p2` ukazuje, že data JSON byla správně zserializována.</span><span class="sxs-lookup"><span data-stu-id="f96c9-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f96c9-116">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f96c9-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f96c9-117">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f96c9-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f96c9-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f96c9-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f96c9-119">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f96c9-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f96c9-120">Chcete-li nastavit, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f96c9-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="f96c9-121">Vytvořte řešení JsonSerialization.sln, jak je popsáno v [sestavení ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f96c9-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f96c9-122">Spusťte výslednou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f96c9-122">Run the resulting console application.</span></span>  
