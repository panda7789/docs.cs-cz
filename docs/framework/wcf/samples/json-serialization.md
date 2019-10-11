---
title: Ukázka DataContractJsonSerializer
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 1711c826397dfb8b54ecedee08e88e67cb58d2a4
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180232"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="7d415-102">Ukázka DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="7d415-102">DataContractJsonSerializer sample</span></span>
<span data-ttu-id="7d415-103">Tato ukázka předvádí, jak použít <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci dat ve formátu JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="7d415-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="7d415-104">Tento modul serializace převede data JSON na instance .NET Frameworkch typů a vrátí se zpět do dat JSON.</span><span class="sxs-lookup"><span data-stu-id="7d415-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="7d415-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7d415-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="7d415-106">Formát dat JSON je zvláště užitečný při psaní asynchronních webových aplikací ve stylu JavaScript a XML (AJAX).</span><span class="sxs-lookup"><span data-stu-id="7d415-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="7d415-107">Podpora AJAX v Windows Communication Foundation (WCF) je optimalizována pro použití s ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="7d415-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="7d415-108">Příklady použití Windows Communication Foundation (WCF) s ASP.NET AJAX naleznete v [ukázkách AJAX](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="7d415-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d415-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7d415-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7d415-110">Ukázka používá ke znázornění serializace a deserializace kontrakt dat `Person`.</span><span class="sxs-lookup"><span data-stu-id="7d415-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="7d415-111">Chcete-li serializovat instanci typu `Person` na JSON, nejprve vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> a použijte metodu `WriteObject` pro zápis dat JSON do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="7d415-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="7d415-112">Proud paměti obsahuje platná data JSON.</span><span class="sxs-lookup"><span data-stu-id="7d415-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="7d415-113">Ukázka demonstruje deserializaci z dat JSON do objektu.</span><span class="sxs-lookup"><span data-stu-id="7d415-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="7d415-114">Potom datový proud převinete a zavoláte `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="7d415-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="7d415-115">Prozkoumání objektu `p2` odhalí, že data JSON byla správně deserializována.</span><span class="sxs-lookup"><span data-stu-id="7d415-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7d415-116">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="7d415-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7d415-117">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="7d415-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7d415-118">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pro stažení ukázek Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7d415-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7d415-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7d415-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7d415-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="7d415-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="7d415-121">Sestavte řešení JsonSerialization. sln, jak je popsáno v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7d415-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="7d415-122">Spusťte výslednou konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d415-122">Run the resulting console application.</span></span>  
