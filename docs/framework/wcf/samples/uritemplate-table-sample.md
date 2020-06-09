---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: ff88bdfe0c8c32da6f07f2b22de54af437376c51
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596432"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="8b680-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8b680-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="8b680-103"><xref:System.UriTemplateTable>Třída poskytuje tabulkovou strukturu asociativní tabulky pro práci se sadou `UriTemplate` instancí.</span><span class="sxs-lookup"><span data-stu-id="8b680-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="8b680-104">Konkrétní identifikátory URI (Uniform Resource Identifier) lze efektivně porovnat proti všem šablonám v tabulce a data přidružená k odpovídající šabloně lze načíst.</span><span class="sxs-lookup"><span data-stu-id="8b680-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="8b680-105">Tato ukázka demonstruje následující klíčové koncepty týkající se `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="8b680-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="8b680-106">Syntaxe pro vytvoření instance `UriTemplateTable` .</span><span class="sxs-lookup"><span data-stu-id="8b680-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="8b680-107">Naplnění `UriTemplateTable` se sadou párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="8b680-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="8b680-108">Odpovídá kandidátu identifikátoru URI na tabulku pomocí <xref:System.UriTemplateTable.MatchSingle%2A> .</span><span class="sxs-lookup"><span data-stu-id="8b680-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b680-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8b680-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8b680-110">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b680-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="8b680-111">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8b680-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8b680-112">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="8b680-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8b680-113">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8b680-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8b680-114">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="8b680-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b680-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8b680-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="8b680-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b680-116">See also</span></span>

- [<span data-ttu-id="8b680-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8b680-117">UriTemplate Table Dispatcher</span></span>](uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="8b680-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8b680-118">UriTemplate</span></span>](uritemplate-sample.md)
