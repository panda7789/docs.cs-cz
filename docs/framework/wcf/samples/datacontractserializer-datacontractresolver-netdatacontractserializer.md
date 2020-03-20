---
title: Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144979"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="d681a-102">Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="d681a-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="d681a-103">Tato ukázka ukazuje, <xref:System.Runtime.Serialization.DataContractSerializer> jak použití <xref:System.Runtime.Serialization.DataContractResolver> s vhodné poskytuje <xref:System.Runtime.Serialization.NetDataContractSerializer>stejné funkce jako .</span><span class="sxs-lookup"><span data-stu-id="d681a-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="d681a-104">Tato ukázka ukazuje, <xref:System.Runtime.Serialization.DataContractResolver> jak vytvořit vhodné a <xref:System.Runtime.Serialization.DataContractSerializer>jak ji přidat do .</span><span class="sxs-lookup"><span data-stu-id="d681a-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="d681a-105">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="d681a-105">Sample details</span></span>
 <span data-ttu-id="d681a-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>se liší <xref:System.Runtime.Serialization.DataContractSerializer> jedním důležitým <xref:System.Runtime.Serialization.NetDataContractSerializer> způsobem: zahrnuje informace o typu CLR <xref:System.Runtime.Serialization.DataContractSerializer> v serializovaném XML, zatímco není.</span><span class="sxs-lookup"><span data-stu-id="d681a-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="d681a-107">Proto <xref:System.Runtime.Serialization.NetDataContractSerializer> lze použít pouze v případě, že serializace a deserializace končí sdílet stejné typy CLR.</span><span class="sxs-lookup"><span data-stu-id="d681a-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="d681a-108">Doporučuje se však <xref:System.Runtime.Serialization.DataContractSerializer> používat, protože jeho <xref:System.Runtime.Serialization.NetDataContractSerializer>výkon je lepší než .</span><span class="sxs-lookup"><span data-stu-id="d681a-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="d681a-109">Informace, které jsou serializovány <xref:System.Runtime.Serialization.DataContractSerializer> v <xref:System.Runtime.Serialization.DataContractResolver> souboru přidáním a k němu.</span><span class="sxs-lookup"><span data-stu-id="d681a-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="d681a-110">Tato ukázka se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="d681a-110">This sample consists of two projects.</span></span> <span data-ttu-id="d681a-111">První projekt <xref:System.Runtime.Serialization.NetDataContractSerializer> používá serializovat objekt.</span><span class="sxs-lookup"><span data-stu-id="d681a-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="d681a-112">Druhý projekt <xref:System.Runtime.Serialization.DataContractSerializer> používá <xref:System.Runtime.Serialization.DataContractResolver> s poskytnout stejné funkce jako první projekt.</span><span class="sxs-lookup"><span data-stu-id="d681a-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="d681a-113">Následující příklad kódu ukazuje implementaci <xref:System.Runtime.Serialization.DataContractResolver> vlastního `MyDataContractResolver` s názvem, <xref:System.Runtime.Serialization.DataContractSerializer> který je přidán do projektu DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="d681a-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        type ??= Type.GetType(typeName + ", " + typeNamespace);
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="d681a-114">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="d681a-114">To use this sample</span></span>

1. <span data-ttu-id="d681a-115">Pomocí Visual Studia 2012 otevřete soubor řešení DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="d681a-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="d681a-116">Klepněte pravým tlačítkem myši na soubor řešení a zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="d681a-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="d681a-117">V dialogovém okně **Stránky vlastností řešení** vyberte v části **Společné vlastnosti** **projekt po spuštění** **položku Více projektů při spuštění:**.</span><span class="sxs-lookup"><span data-stu-id="d681a-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="d681a-118">Vedle projektu **DCSwithDCR** vyberte v rozevíracím seznamu **Akce** možnost **Začít.**</span><span class="sxs-lookup"><span data-stu-id="d681a-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="d681a-119">Vedle projektu **NetDCS** vyberte v rozevíracím souboru **Akce** možnost **Zahájit.**</span><span class="sxs-lookup"><span data-stu-id="d681a-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="d681a-120">Klepnutím na **tlačítko OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="d681a-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="d681a-121">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d681a-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="d681a-122">Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="d681a-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d681a-123">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d681a-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d681a-124">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d681a-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d681a-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d681a-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d681a-126">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d681a-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
