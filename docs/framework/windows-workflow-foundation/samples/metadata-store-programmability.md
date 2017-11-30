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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b38aec2e3f06e1f998bbc042c70909d208d3b63
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2017
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="42935-102">Programovatelnosti úložiště metadat</span><span class="sxs-lookup"><span data-stu-id="42935-102">Metadata Store Programmability</span></span>
<span data-ttu-id="42935-103">Metadata úložiště je [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkce, která umožňuje pro přidružení libovolný metadata, a to ve formě CLR atributy, typy za běhu.</span><span class="sxs-lookup"><span data-stu-id="42935-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="42935-104">To umožňuje volné párování mezi komponenty Runtime a jejich protějšky v době návrhu a také možnost měnit součásti návrhu bez ovlivnění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="42935-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="42935-105">Ukázka ukazuje, jak program proti úložišti metadat aplikací běhového typu zdroje, pro kterou jsme nemají žádnou kontrolu nad atributů.</span><span class="sxs-lookup"><span data-stu-id="42935-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="42935-106">Terminologie obvykle používaných je, že hostitelskou aplikaci zaregistruje metadata pro sadu typů.</span><span class="sxs-lookup"><span data-stu-id="42935-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="42935-107">V rámci výstupu, můžete si povšimnout atribut další, neočekávané <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="42935-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="42935-108">Tím se přidá při použití metadat rozhraní API a nemá žádný vliv na spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="42935-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="42935-109">Tento příklad znázorňuje:</span><span class="sxs-lookup"><span data-stu-id="42935-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="42935-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="42935-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="42935-111">Atribut vkládání pomocí metadat ukládat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="42935-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="42935-112">Odložení metadata registrace pomocí mechanismus zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="42935-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42935-113">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="42935-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="42935-114">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="42935-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="42935-115">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="42935-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="42935-116">Pokud chcete spustit řešení, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="42935-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="42935-117">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="42935-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="42935-118">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="42935-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="42935-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="42935-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42935-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="42935-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`