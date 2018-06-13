---
title: Serializace JSON
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 389bdc8b064bda9870b33a2e4c46fdf90bb7f3ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502507"
---
# <a name="json-serialization"></a><span data-ttu-id="438d0-102">Serializace JSON</span><span class="sxs-lookup"><span data-stu-id="438d0-102">JSON Serialization</span></span>
<span data-ttu-id="438d0-103">Tento příklad znázorňuje způsob použití <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> k serializaci a deserializaci data ve formátu JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="438d0-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="438d0-104">Tento modul serializace převádí JSON data do instance [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy a zpět do JSON data.</span><span class="sxs-lookup"><span data-stu-id="438d0-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="438d0-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> podporuje stejné typy jako <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="438d0-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="438d0-106">Formát dat JSON je obzvláště užitečná při psaní asynchronní JavaScript a XML (AJAX)-styl webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="438d0-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="438d0-107">Podpora jazyka AJAX ve Windows Communication Foundation (WCF) je optimalizovaný pro použití s prvku ASP.NET AJAX prostřednictvím ovládací prvek ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="438d0-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="438d0-108">Příklady, jak používat Windows Communication Foundation (WCF) pomocí prvku ASP.NET AJAX, najdete v článku [AJAX ukázky](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="438d0-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="438d0-109">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="438d0-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="438d0-110">Ukázce se používá `Person` kontraktů dat k předvedení serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="438d0-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="438d0-111">K serializaci instanci `Person` zadejte do formátu JSON, vytvořte <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> první a použít `WriteObject` metoda při zápisu dat JSON na datový proud.</span><span class="sxs-lookup"><span data-stu-id="438d0-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="438d0-112">Datový proud paměti obsahuje platná data JSON.</span><span class="sxs-lookup"><span data-stu-id="438d0-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="438d0-113">Ukázka ukazuje deserializaci z dat JSON na objekt.</span><span class="sxs-lookup"><span data-stu-id="438d0-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="438d0-114">Potom rewind datového proudu a volání `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="438d0-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="438d0-115">Zkoumání `p2` objekt zjistí, zda byl správně deserializovat JSON data.</span><span class="sxs-lookup"><span data-stu-id="438d0-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="438d0-116">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="438d0-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="438d0-117">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="438d0-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="438d0-118">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="438d0-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="438d0-119">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="438d0-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="438d0-120">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="438d0-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="438d0-121">Sestavte řešení JsonSerialization.sln, jak je popsáno v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="438d0-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="438d0-122">Spusťte výsledné konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="438d0-122">Run the resulting console application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="438d0-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="438d0-123">See Also</span></span>
