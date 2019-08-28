---
title: Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: d7102e60c8b5302d4f3bc83b356dbc7de117f57a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039867"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f8e3b-102">Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f8e3b-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f8e3b-103">Tato ukázka předvádí, jak použití <xref:System.Runtime.Serialization.DataContractSerializer> s vhodnou <xref:System.Runtime.Serialization.DataContractResolver> funkcí poskytuje stejné funkce jako <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f8e3b-104">V této ukázce se dozvíte, jak <xref:System.Runtime.Serialization.DataContractResolver> vytvořit odpovídající a jak ho přidat <xref:System.Runtime.Serialization.DataContractSerializer>do.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="f8e3b-105">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="f8e3b-105">Sample details</span></span>
 <span data-ttu-id="f8e3b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>se liší od <xref:System.Runtime.Serialization.DataContractSerializer> v jednom důležitém způsobu <xref:System.Runtime.Serialization.NetDataContractSerializer> : obsahuje informace o typu CLR v serializovaném kódu <xref:System.Runtime.Serialization.DataContractSerializer> XML, zatímco ne.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f8e3b-107">Proto lze <xref:System.Runtime.Serialization.NetDataContractSerializer> použít pouze v případě, že serializace a deserializace ukončí sdílení stejných typů CLR.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f8e3b-108">Doporučuje se však použít <xref:System.Runtime.Serialization.DataContractSerializer> , protože jeho výkon je lepší než. <xref:System.Runtime.Serialization.NetDataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="f8e3b-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f8e3b-109">Informace, které jsou serializovány <xref:System.Runtime.Serialization.DataContractSerializer> , lze změnit <xref:System.Runtime.Serialization.DataContractResolver> přidáním do ní.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="f8e3b-110">Tato ukázka se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-110">This sample consists of two projects.</span></span> <span data-ttu-id="f8e3b-111">První projekt používá <xref:System.Runtime.Serialization.NetDataContractSerializer> k serializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f8e3b-112">Druhý projekt používá <xref:System.Runtime.Serialization.DataContractSerializer> s a <xref:System.Runtime.Serialization.DataContractResolver> k poskytnutí stejných funkcí jako první projekt.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="f8e3b-113">Následující příklad kódu ukazuje implementaci vlastního <xref:System.Runtime.Serialization.DataContractResolver> názvu `MyDataContractResolver` <xref:System.Runtime.Serialization.DataContractSerializer> , který je přidán do v projektu DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

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
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
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

#### <a name="to-use-this-sample"></a><span data-ttu-id="f8e3b-114">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="f8e3b-114">To use this sample</span></span>

1. <span data-ttu-id="f8e3b-115">Pomocí sady Visual Studio 2012 otevřete soubor řešení DCRSample. sln.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="f8e3b-116">Klikněte pravým tlačítkem na soubor řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="f8e3b-117">V dialogovém okně **stránky vlastností řešení** v části **společné vlastnosti**, **spouštěný projekt**vyberte **více projektů po spuštění:** .</span><span class="sxs-lookup"><span data-stu-id="f8e3b-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="f8e3b-118">Vedle projektu **DCSwithDCR** vyberte v rozevíracím seznamu **Akce** možnost **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="f8e3b-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="f8e3b-119">Vedle projektu **NetDCS** vyberte v rozevíracím seznamu **Akce** možnost **Spustit** .</span><span class="sxs-lookup"><span data-stu-id="f8e3b-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="f8e3b-120">Kliknutím na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="f8e3b-121">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="f8e3b-122">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8e3b-123">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f8e3b-124">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-124">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f8e3b-125">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f8e3b-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f8e3b-126">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
