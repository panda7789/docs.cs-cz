---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 724a13504cea2672aef7ff155fbbff055aac34e6
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044580"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="61172-102">Ukázka dispečera tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="61172-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="61172-103">Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se <xref:System.UriTemplate> sadou instancí. <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="61172-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="61172-104">Tato ukázka předvádí základní modul pro expedici sestavený `UriTemplateTable`pomocí, společný scénář použití `UriTemplateTable` pro třídu.</span><span class="sxs-lookup"><span data-stu-id="61172-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="61172-105">Tato ukázka demonstruje následující klíčové koncepty pro `UriTemplateTable` třídu:</span><span class="sxs-lookup"><span data-stu-id="61172-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="61172-106">Přidružení delegátů k `UriTemplates` `UriTemplateTable`v.</span><span class="sxs-lookup"><span data-stu-id="61172-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="61172-107">Použijte <xref:System.UriTemplateTable.MatchSingle%2A> k získání správného delegáta obslužné rutiny pro konkrétní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="61172-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="61172-108">Volání delegáta obslužné rutiny pro zpracování žádosti.</span><span class="sxs-lookup"><span data-stu-id="61172-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="61172-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="61172-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="61172-110">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61172-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="61172-111">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61172-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="61172-112">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="61172-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61172-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="61172-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="61172-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="61172-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61172-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="61172-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="61172-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61172-116">See also</span></span>

- [<span data-ttu-id="61172-117">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="61172-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="61172-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="61172-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
