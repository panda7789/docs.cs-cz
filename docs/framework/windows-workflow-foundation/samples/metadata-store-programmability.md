---
title: "Programovatelnosti úložiště metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01d51c9727847f00bdcf3f62945207882e3f41d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="ed4c9-102">Programovatelnosti úložiště metadat</span><span class="sxs-lookup"><span data-stu-id="ed4c9-102">Metadata Store Programmability</span></span>
<span data-ttu-id="ed4c9-103">Metadata úložiště je [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkce, která umožňuje pro přidružení libovolný metadata, a to ve formě CLR atributy, typy za běhu.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="ed4c9-104">To umožňuje volné párování mezi komponenty Runtime a jejich protějšky v době návrhu a také možnost měnit součásti návrhu bez ovlivnění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="ed4c9-105">Ukázka ukazuje, jak program proti úložišti metadat aplikací běhového typu zdroje, pro kterou jsme nemají žádnou kontrolu nad atributů.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="ed4c9-106">Terminologie obvykle používaných je, že hostitelskou aplikaci zaregistruje metadata pro sadu typů.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="ed4c9-107">V rámci výstupu, můžete si povšimnout atribut další, neočekávané <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="ed4c9-108">Tím se přidá při použití metadat rozhraní API a nemá žádný vliv na spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="ed4c9-109">Tento příklad znázorňuje:</span><span class="sxs-lookup"><span data-stu-id="ed4c9-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="ed4c9-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="ed4c9-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="ed4c9-111">Atribut vkládání pomocí metadat ukládat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="ed4c9-112">Odložení metadata registrace pomocí mechanismus zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed4c9-113">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="ed4c9-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ed4c9-114">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="ed4c9-115">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ed4c9-116">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed4c9-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed4c9-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="ed4c9-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed4c9-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed4c9-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ed4c9-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`