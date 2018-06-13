---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: ef445e30257e9bf99e111c1a1f569e42c2017b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504195"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="05e3f-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="05e3f-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="05e3f-103"><xref:System.UriTemplateTable> Třída poskytuje strukturu asociativní tabulky jako slovník pro práci s sadu `UriTemplate` instance.</span><span class="sxs-lookup"><span data-stu-id="05e3f-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="05e3f-104">Konkrétní identifikátory Uniform Resource (Identifier) je možné porovnávat efektivně proti všechny šablony v tabulce a dá se načíst data přidružená k šabloně odpovídající.</span><span class="sxs-lookup"><span data-stu-id="05e3f-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="05e3f-105">Tento příklad znázorňuje následující klíčové koncepty související s `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="05e3f-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="05e3f-106">Syntaxe pro vytváření instancí `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="05e3f-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="05e3f-107">Sestavování `UriTemplateTable` s sada párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="05e3f-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="05e3f-108">Odpovídající kandidátem URI před použitím tabulky <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="05e3f-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="05e3f-109">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="05e3f-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="05e3f-110">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05e3f-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="05e3f-111">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="05e3f-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="05e3f-112">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="05e3f-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="05e3f-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="05e3f-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="05e3f-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="05e3f-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="05e3f-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="05e3f-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="05e3f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="05e3f-116">See Also</span></span>  
 [<span data-ttu-id="05e3f-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="05e3f-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="05e3f-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="05e3f-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
