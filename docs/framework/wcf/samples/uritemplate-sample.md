---
title: Ukázka UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: fb956882ae653f584026fefb20e261c90010ca9b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591056"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="ef133-102">Ukázka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ef133-102">UriTemplate Sample</span></span>
<span data-ttu-id="ef133-103"><xref:System.UriTemplate>Třída poskytuje metody pro práci se sadami identifikátorů URI, které sdílejí společnou strukturu.</span><span class="sxs-lookup"><span data-stu-id="ef133-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="ef133-104">Tato ukázka demonstruje následující klíčové koncepty týkající se `UriTemplate` :</span><span class="sxs-lookup"><span data-stu-id="ef133-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="ef133-105">Syntaxe pro vytváření šablon</span><span class="sxs-lookup"><span data-stu-id="ef133-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="ef133-106">Vytváření instancí identifikátorů URI z `UriTemplate` pomocí <xref:System.UriTemplate.BindByName%2A> a <xref:System.UriTemplate.BindByPosition%2A> .</span><span class="sxs-lookup"><span data-stu-id="ef133-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="ef133-107"><xref:System.UriTemplateTable.Match%2A>, což je inverzní operace `BindByName` a `BindByPosition` .</span><span class="sxs-lookup"><span data-stu-id="ef133-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef133-108">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ef133-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ef133-109">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef133-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="ef133-110">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ef133-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef133-111">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="ef133-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ef133-112">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ef133-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ef133-113">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="ef133-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef133-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ef133-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="ef133-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef133-115">See also</span></span>

- [<span data-ttu-id="ef133-116">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ef133-116">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="ef133-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="ef133-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
