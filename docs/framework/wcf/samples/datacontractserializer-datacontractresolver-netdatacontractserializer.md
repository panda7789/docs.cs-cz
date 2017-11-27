---
title: "Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d189b68cc8321dace0418a3c1e4b1b3c21cfd3ae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="16245-102">Použití DataContractSerializer a DataContractResolver pro zajištění funkcí NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="16245-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="16245-103">Tento příklad znázorňuje způsob použití <xref:System.Runtime.Serialization.DataContractSerializer> odpovídajícími <xref:System.Runtime.Serialization.DataContractResolver> poskytuje stejné funkce jako <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16245-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="16245-104">Tento příklad ukazuje postup vytvoření odpovídající <xref:System.Runtime.Serialization.DataContractResolver> a jak ho přidat do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16245-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="16245-105">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="16245-105">Sample details</span></span>  
 <span data-ttu-id="16245-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>se liší od <xref:System.Runtime.Serialization.DataContractSerializer> jedním způsobem důležité: <xref:System.Runtime.Serialization.NetDataContractSerializer> obsahuje informace o typu CLR v serializovaných XML, zatímco <xref:System.Runtime.Serialization.DataContractSerializer> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="16245-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="16245-107">Proto <xref:System.Runtime.Serialization.NetDataContractSerializer> lze použít pouze v případě, že jak serializaci a deserializaci končí sdílet stejné typy CLR.</span><span class="sxs-lookup"><span data-stu-id="16245-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="16245-108">Doporučujeme však používat <xref:System.Runtime.Serialization.DataContractSerializer> vzhledem k tomu, že je lepší, než jeho výkon <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16245-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="16245-109">Můžete změnit informace, které je serializována v <xref:System.Runtime.Serialization.DataContractSerializer> přidáním <xref:System.Runtime.Serialization.DataContractResolver> k němu.</span><span class="sxs-lookup"><span data-stu-id="16245-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>  
  
 <span data-ttu-id="16245-110">Tato ukázka se skládá ze dvou projektů.</span><span class="sxs-lookup"><span data-stu-id="16245-110">This sample consists of two projects.</span></span> <span data-ttu-id="16245-111">První projekt používá <xref:System.Runtime.Serialization.NetDataContractSerializer> o serializaci objektu.</span><span class="sxs-lookup"><span data-stu-id="16245-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="16245-112">Druhý projektu používá <xref:System.Runtime.Serialization.DataContractSerializer> s <xref:System.Runtime.Serialization.DataContractResolver> nabízí stejné funkce jako první projekt.</span><span class="sxs-lookup"><span data-stu-id="16245-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>  
  
 <span data-ttu-id="16245-113">Následující příklad kódu ukazuje implementaci vlastní <xref:System.Runtime.Serialization.DataContractResolver> s názvem `MyDataContractResolver` který je přidán do <xref:System.Runtime.Serialization.DataContractSerializer> v DCSwithDCR projektu.</span><span class="sxs-lookup"><span data-stu-id="16245-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>  
  
```  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="16245-114">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="16245-114">To use this sample</span></span>  
  
1.  <span data-ttu-id="16245-115">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení DCRSample.sln.</span><span class="sxs-lookup"><span data-stu-id="16245-115">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the DCRSample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="16245-116">Klikněte pravým tlačítkem na soubor řešení a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="16245-116">Right-click the solution file and choose **Properties**.</span></span>  
  
3.  <span data-ttu-id="16245-117">V **stránky vlastností řešení** dialogové okno, v části **společných vlastností**, **spouštěný projekt**, vyberte **více projektů po spuštění:**.</span><span class="sxs-lookup"><span data-stu-id="16245-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>  
  
4.  <span data-ttu-id="16245-118">Vedle položky **DCSwithDCR** projekt, vyberte **spustit** z **akce** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="16245-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>  
  
5.  <span data-ttu-id="16245-119">Vedle položky **NetDCS** projekt, vyberte **spustit** z **akce** rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="16245-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>  
  
6.  <span data-ttu-id="16245-120">Klikněte na tlačítko **OK** zavřete dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="16245-120">Click **OK** to close the dialog.</span></span>  
  
7.  <span data-ttu-id="16245-121">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="16245-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
8.  <span data-ttu-id="16245-122">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="16245-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16245-123">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="16245-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="16245-124">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="16245-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16245-125">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="16245-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16245-126">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="16245-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a><span data-ttu-id="16245-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="16245-127">See Also</span></span>
