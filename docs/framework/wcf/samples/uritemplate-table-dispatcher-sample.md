---
title: Ukázka dispečera tabulky UriTemplate
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 97e916aaf9d137eb7931470f9565797b03620d28
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591069"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="e24ba-102">Ukázka dispečera tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e24ba-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="e24ba-103"><xref:System.UriTemplateTable>Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se sadou <xref:System.UriTemplate> instancí.</span><span class="sxs-lookup"><span data-stu-id="e24ba-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="e24ba-104">Tato ukázka předvádí základní modul pro expedici sestavený pomocí `UriTemplateTable` , společný scénář použití pro `UriTemplateTable` třídu.</span><span class="sxs-lookup"><span data-stu-id="e24ba-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="e24ba-105">Tato ukázka demonstruje následující klíčové koncepty pro `UriTemplateTable` třídu:</span><span class="sxs-lookup"><span data-stu-id="e24ba-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="e24ba-106">Přidružení delegátů k `UriTemplates` v `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="e24ba-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="e24ba-107">Použijte <xref:System.UriTemplateTable.MatchSingle%2A> k získání správného delegáta obslužné rutiny pro konkrétní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="e24ba-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="e24ba-108">Volání delegáta obslužné rutiny pro zpracování žádosti.</span><span class="sxs-lookup"><span data-stu-id="e24ba-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e24ba-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e24ba-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e24ba-110">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e24ba-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e24ba-111">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e24ba-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e24ba-112">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="e24ba-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e24ba-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e24ba-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e24ba-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="e24ba-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e24ba-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e24ba-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="e24ba-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e24ba-116">See also</span></span>

- [<span data-ttu-id="e24ba-117">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e24ba-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="e24ba-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="e24ba-118">UriTemplate</span></span>](uritemplate-sample.md)
