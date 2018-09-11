---
title: Programovatelnost Store metadat
ms.date: 03/30/2017
ms.assetid: 5b613661-f3f9-4e07-8e88-28c9ea2fd8f8
ms.openlocfilehash: 4ea6117686b985a9ea18ce4e5cc4ea2b5c25524c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276325"
---
# <a name="metadata-store-programmability"></a><span data-ttu-id="7da72-102">Programovatelnost Store metadat</span><span class="sxs-lookup"><span data-stu-id="7da72-102">Metadata Store Programmability</span></span>
<span data-ttu-id="7da72-103">Metadata úložiště je [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] funkce, která umožňuje přidružení libovolného metadat ve formě CLR atributy pro typy v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7da72-103">The metadata store is a [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] feature that allows for the association of arbitrary metadata, in the form of CLR attributes, to types at runtime.</span></span> <span data-ttu-id="7da72-104">To umožňuje volné párování mezi běhové komponenty a jejich protějšky v době návrhu, jakož i změnit komponenty doby návrhu, aniž by to ovlivnilo modul runtime.</span><span class="sxs-lookup"><span data-stu-id="7da72-104">This allows for a loose coupling between the run-time components and their design-time counterparts, as well as the ability to change the design-time components without affecting the runtime.</span></span> <span data-ttu-id="7da72-105">Vzorek ukazuje, jak programovat proti úložišti metadat s použitím atributů typu za běhu, u kterého jsme nemají žádnou kontrolu nad zdroji.</span><span class="sxs-lookup"><span data-stu-id="7da72-105">The sample shows how to program against the metadata store by applying attributes to a run-time type, the source for which we have no control over.</span></span> <span data-ttu-id="7da72-106">Terminologie obvykle používá je, že hostitelské aplikace registruje metadata pro sadu typů.</span><span class="sxs-lookup"><span data-stu-id="7da72-106">The terminology typically used is that a hosting application registers the metadata for a set of types.</span></span>  
  
 <span data-ttu-id="7da72-107">V rámci výstupu, můžete si všimnout atribut další, neočekávané <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span><span class="sxs-lookup"><span data-stu-id="7da72-107">Within the output, you may notice an additional, unexpected attribute, <!--zz <xref:System.Runtime.InteropServices.GUIDAttribute> --> `System.Runtime.InteropServices.GUIDAttribute`.</span></span> <span data-ttu-id="7da72-108">Tím se přidá při používání metadat rozhraní API a nemá žádný vliv na spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="7da72-108">This is added when using the Metadata API and has no impact on the running of the sample.</span></span>  
  
 <span data-ttu-id="7da72-109">V této ukázce:</span><span class="sxs-lookup"><span data-stu-id="7da72-109">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7da72-110">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="7da72-110">Demonstrates</span></span>  
  
-   <span data-ttu-id="7da72-111">Uložit atribut vkládání pomocí metadat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7da72-111">Attribute injection using the metadata store API.</span></span>  
  
-   <span data-ttu-id="7da72-112">Odložení metadat registrace pomocí mechanismu zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7da72-112">Using a callback mechanism to defer metadata registration.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7da72-113">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="7da72-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7da72-114">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ProgrammingMetadataStore.sln.</span><span class="sxs-lookup"><span data-stu-id="7da72-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ProgrammingMetadataStore.sln solution file.</span></span>  
  
2.  <span data-ttu-id="7da72-115">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="7da72-115">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="7da72-116">Abyste mohli spustit řešení, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="7da72-116">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7da72-117">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="7da72-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7da72-118">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7da72-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7da72-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7da72-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7da72-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7da72-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\MetadataStore`