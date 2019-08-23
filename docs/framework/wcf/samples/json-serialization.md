---
title: Serializace JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 9b1e20c6262f286a4b81f8c368a153fb5a26193b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913962"
---
# <a name="json-serialization"></a><span data-ttu-id="2a54b-102">Serializace JSON</span><span class="sxs-lookup"><span data-stu-id="2a54b-102">JSON Serialization</span></span>
<span data-ttu-id="2a54b-103">Tato ukázka demonstruje, jak <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> použít k serializaci a deserializaci dat ve formátu JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="2a54b-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="2a54b-104">Tento modul serializace převede data JSON na instance .NET Frameworkch typů a vrátí se zpět do dat JSON.</span><span class="sxs-lookup"><span data-stu-id="2a54b-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="2a54b-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2a54b-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="2a54b-106">Formát dat JSON je zvláště užitečný při psaní asynchronních webových aplikací ve stylu JavaScript a XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="2a54b-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="2a54b-107">Podpora AJAX v Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="2a54b-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="2a54b-108">Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2a54b-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a54b-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="2a54b-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2a54b-110">Ukázka používá `Person` kontrakt dat k demonstraci serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="2a54b-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="2a54b-111">Chcete-li serializovat instanci `Person` typu na JSON, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> vytvořte první a použijte `WriteObject` metodu pro zápis dat JSON do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="2a54b-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="2a54b-112">Proud paměti obsahuje platná data JSON.</span><span class="sxs-lookup"><span data-stu-id="2a54b-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="2a54b-113">Ukázka demonstruje deserializaci z dat JSON do objektu.</span><span class="sxs-lookup"><span data-stu-id="2a54b-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="2a54b-114">Pak můžete Stream převinout zpět a zavolat `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="2a54b-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="2a54b-115">Prozkoumáním `p2` objektu zjistíte, že data JSON byla deserializována správně.</span><span class="sxs-lookup"><span data-stu-id="2a54b-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2a54b-116">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="2a54b-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a54b-117">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2a54b-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2a54b-118">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="2a54b-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a54b-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2a54b-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2a54b-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2a54b-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="2a54b-121">Sestavte řešení JsonSerialization. sln, jak je popsáno v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2a54b-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2a54b-122">Spusťte výslednou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2a54b-122">Run the resulting console application.</span></span>  
