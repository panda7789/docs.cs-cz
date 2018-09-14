---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 4a4f725e88e014da241e1042c27bfee270e13268
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521021"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="4847f-102">Ukázka dispečera tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4847f-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="4847f-103"><xref:System.UriTemplateTable> Třída poskytuje strukturu jako slovník asociativní tabulky pro práci se sadou <xref:System.UriTemplate> instancí.</span><span class="sxs-lookup"><span data-stu-id="4847f-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="4847f-104">Tato ukázka demonstruje základní dispatching modul vyvíjené `UriTemplateTable`, běžný scénář využití pro `UriTemplateTable` třídy.</span><span class="sxs-lookup"><span data-stu-id="4847f-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="4847f-105">Tato ukázka demonstruje následující klíčové koncepty `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="4847f-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="4847f-106">Přidružování delegátů pomocí `UriTemplates` v `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="4847f-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="4847f-107">Pomocí <xref:System.UriTemplateTable.MatchSingle%2A> získat správný obslužné rutiny delegáta pro konkrétní identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="4847f-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
-   <span data-ttu-id="4847f-108">Vyvolání delegáta obslužné rutiny pro zpracování žádosti.</span><span class="sxs-lookup"><span data-stu-id="4847f-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4847f-109">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="4847f-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4847f-110">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4847f-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="4847f-111">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4847f-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4847f-112">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="4847f-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4847f-113">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4847f-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4847f-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4847f-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4847f-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4847f-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="4847f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4847f-116">See Also</span></span>  
 [<span data-ttu-id="4847f-117">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4847f-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="4847f-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="4847f-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
