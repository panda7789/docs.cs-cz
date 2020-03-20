---
title: Ukázková tabulka UriTemplate
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: c0aed1a49faf74ab9fd463769aab66ad72e74038
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183256"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="a2008-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a2008-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="a2008-103">Třída <xref:System.UriTemplateTable> poskytuje slovníkjako asociativní tabulka strukturu pro práci `UriTemplate` se sadou instancí.</span><span class="sxs-lookup"><span data-stu-id="a2008-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="a2008-104">Specifické identifikátory prostředků (URI) lze efektivně porovnat se všemi šablonami v tabulce a lze je načíst data přidružená k odpovídající šabloně.</span><span class="sxs-lookup"><span data-stu-id="a2008-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="a2008-105">Tato ukázka ukazuje následující klíčové pojmy vztahující se k `UriTemplateTable` třídě:</span><span class="sxs-lookup"><span data-stu-id="a2008-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="a2008-106">Syntaxe pro vytvoření `UriTemplateTable`instance rozhraní .</span><span class="sxs-lookup"><span data-stu-id="a2008-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="a2008-107">Naplnění a `UriTemplateTable` se sadou párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="a2008-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="a2008-108">Porovnávání identifikátoru URI <xref:System.UriTemplateTable.MatchSingle%2A>kandidáta s tabulkami pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="a2008-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a2008-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="a2008-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a2008-110">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a2008-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="a2008-111">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a2008-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a2008-112">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="a2008-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a2008-113">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="a2008-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a2008-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a2008-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2008-115">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a2008-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="a2008-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2008-116">See also</span></span>

- [<span data-ttu-id="a2008-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a2008-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="a2008-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="a2008-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
