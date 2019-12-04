---
title: Ukázka UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: c9dd8bdd21a075dca590c9446808860c006c18f8
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715427"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="f9fb5-102">Ukázka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f9fb5-102">UriTemplate Sample</span></span>
<span data-ttu-id="f9fb5-103">Třída <xref:System.UriTemplate> poskytuje metody pro práci se sadami identifikátorů URI, které sdílejí společnou strukturu.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="f9fb5-104">Tato ukázka demonstruje následující klíčové koncepty týkající se `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="f9fb5-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="f9fb5-105">Syntaxe pro vytváření šablon</span><span class="sxs-lookup"><span data-stu-id="f9fb5-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="f9fb5-106">Vytváření instancí identifikátorů URI z `UriTemplate` pomocí <xref:System.UriTemplate.BindByName%2A> a <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="f9fb5-107"><xref:System.UriTemplateTable.Match%2A>, což je inverzní operace `BindByName` a `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f9fb5-108">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f9fb5-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f9fb5-109">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9fb5-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f9fb5-110">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f9fb5-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f9fb5-111">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f9fb5-112">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f9fb5-113">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f9fb5-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f9fb5-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="f9fb5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9fb5-115">See also</span></span>

- [<span data-ttu-id="f9fb5-116">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f9fb5-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="f9fb5-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f9fb5-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
