---
title: Serializace JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: c44dd71c3903e5c4d3d37b89881896c65c664262
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591864"
---
# <a name="json-serialization"></a><span data-ttu-id="b91da-102">Serializace JSON</span><span class="sxs-lookup"><span data-stu-id="b91da-102">JSON Serialization</span></span>
<span data-ttu-id="b91da-103">Tato ukázka předvádí, jak používat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci data ve formátu JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="b91da-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="b91da-104">Tato serializační stroj převádí JSON data do instance typů rozhraní .NET Framework a zpět do JSON data.</span><span class="sxs-lookup"><span data-stu-id="b91da-104">This serialization engine converts JSON data into instances of .NET Framework types and back into JSON data.</span></span> <span data-ttu-id="b91da-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b91da-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="b91da-106">Formát dat JSON je obzvláště užitečná při psaní asynchronního JavaScript a XML (AJAX)-stylu webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b91da-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="b91da-107">Podpora pro AJAX ve Windows Communication Foundation (WCF) je optimalizovaná pro použití s technologií ASP.NET AJAX prostřednictvím ovládacího prvku ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="b91da-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="b91da-108">Příklady, jak používat Windows Communication Foundation (WCF) s technologií ASP.NET AJAX, najdete v článku [AJAX ukázky](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="b91da-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b91da-109">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b91da-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b91da-110">Ukázka používá `Person` kontraktů dat k předvedení serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="b91da-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="b91da-111">K serializaci instancí `Person` zadejte do formátu JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použít `WriteObject` metody zapsat JSON data na datový proud.</span><span class="sxs-lookup"><span data-stu-id="b91da-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="b91da-112">Datový proud paměti obsahuje platná data JSON.</span><span class="sxs-lookup"><span data-stu-id="b91da-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="b91da-113">Ukázce deserializaci z dat JSON na objekt.</span><span class="sxs-lookup"><span data-stu-id="b91da-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="b91da-114">Potom rewind datového proudu a volání `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="b91da-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="b91da-115">Zkoumání `p2` objekt odhalí správně deserializovat JSON data.</span><span class="sxs-lookup"><span data-stu-id="b91da-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b91da-116">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="b91da-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b91da-117">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b91da-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b91da-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b91da-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b91da-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b91da-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b91da-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="b91da-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="b91da-121">Sestavte řešení JsonSerialization.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b91da-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="b91da-122">Spuštění výsledné aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="b91da-122">Run the resulting console application.</span></span>  
