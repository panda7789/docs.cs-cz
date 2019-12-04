---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: fb5932acce60e2da45f99730580237d31130d918
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715404"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="3cbbd-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3cbbd-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="3cbbd-103">Třída <xref:System.UriTemplateTable> poskytuje pro práci se sadou instancí `UriTemplate` asociativní strukturu tabulkového typu.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="3cbbd-104">Konkrétní identifikátory URI (Uniform Resource Identifier) lze efektivně porovnat proti všem šablonám v tabulce a data přidružená k odpovídající šabloně lze načíst.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="3cbbd-105">Tato ukázka demonstruje následující klíčové koncepty související s `UriTemplateTable` třídou:</span><span class="sxs-lookup"><span data-stu-id="3cbbd-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="3cbbd-106">Syntaxe pro vytvoření instance `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="3cbbd-107">Naplnění `UriTemplateTable` se sadou párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="3cbbd-108">Porovnání kandidátu identifikátoru URI s tabulkou pomocí <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3cbbd-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3cbbd-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3cbbd-110">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbd-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="3cbbd-111">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3cbbd-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3cbbd-112">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3cbbd-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="3cbbd-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3cbbd-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3cbbd-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="3cbbd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cbbd-116">See also</span></span>

- [<span data-ttu-id="3cbbd-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3cbbd-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="3cbbd-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3cbbd-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
