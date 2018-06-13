---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 9075d779b2ca2360c5ad28c3872c54c64aa200b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506008"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="d49d3-102">Ukázka dispečera tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d49d3-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="d49d3-103"><xref:System.UriTemplateTable> Třída poskytuje strukturu asociativní tabulky jako slovník pro práci s sadu <xref:System.UriTemplate> instance.</span><span class="sxs-lookup"><span data-stu-id="d49d3-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="d49d3-104">Tento příklad znázorňuje modul základní odesílající vytvořená s využitím `UriTemplateTable`, běžné scénáře použití `UriTemplateTable` – třída.</span><span class="sxs-lookup"><span data-stu-id="d49d3-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="d49d3-105">Tento příklad znázorňuje následující klíčové koncepty `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="d49d3-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="d49d3-106">Přidružování delegátů s `UriTemplates` v `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="d49d3-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="d49d3-107">Pomocí <xref:System.UriTemplateTable.MatchSingle%2A> získat delegát správné obslužné rutiny pro konkrétní identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="d49d3-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="d49d3-108">Vyvolání delegáta obslužné rutiny pro zpracování požadavku.</span><span class="sxs-lookup"><span data-stu-id="d49d3-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d49d3-109">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d49d3-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d49d3-110">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d49d3-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="d49d3-111">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d49d3-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d49d3-112">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d49d3-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d49d3-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d49d3-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d49d3-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d49d3-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d49d3-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d49d3-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="d49d3-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d49d3-116">See Also</span></span>  
 [<span data-ttu-id="d49d3-117">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d49d3-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="d49d3-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d49d3-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
