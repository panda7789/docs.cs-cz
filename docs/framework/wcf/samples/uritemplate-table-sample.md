---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 6cd02e5cdf4137efd3254ff1071e5a4a79c2e88a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43658010"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="3824d-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3824d-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="3824d-103"><xref:System.UriTemplateTable> Třída poskytuje strukturu jako slovník asociativní tabulky pro práci se sadou `UriTemplate` instancí.</span><span class="sxs-lookup"><span data-stu-id="3824d-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="3824d-104">Konkrétní Uniform Resource Identifier (identifikátory URI) mohou být efektivně hledána všechny šablony v tabulce, a je možné načíst data přidružená k šabloně odpovídající.</span><span class="sxs-lookup"><span data-stu-id="3824d-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="3824d-105">Tato ukázka demonstruje následující klíčové koncepty týkající `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="3824d-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="3824d-106">Syntaxe pro vytvoření instance `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="3824d-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="3824d-107">Sestavování `UriTemplateTable` sadu dvojic klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="3824d-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="3824d-108">Odpovídající kandidát identifikátor URI pro tabulku s využitím <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="3824d-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3824d-109">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="3824d-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3824d-110">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3824d-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="3824d-111">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3824d-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3824d-112">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3824d-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3824d-113">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3824d-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3824d-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3824d-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3824d-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3824d-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="3824d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3824d-116">See Also</span></span>  
 [<span data-ttu-id="3824d-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3824d-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="3824d-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="3824d-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
