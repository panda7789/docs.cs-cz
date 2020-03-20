---
title: Ukázka UriTemplate
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: e08333235b22e3c24fc6f4855fec43ef8b95fa5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183274"
---
# <a name="uritemplate-sample"></a><span data-ttu-id="853b3-102">Ukázka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="853b3-102">UriTemplate Sample</span></span>
<span data-ttu-id="853b3-103">Třída <xref:System.UriTemplate> poskytuje metody pro práci s sadami IDENTIFIKÁTORŮ, které sdílejí společnou strukturu.</span><span class="sxs-lookup"><span data-stu-id="853b3-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="853b3-104">Tento vzorek ukazuje následující klíčové pojmy `UriTemplate`týkající se :</span><span class="sxs-lookup"><span data-stu-id="853b3-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
- <span data-ttu-id="853b3-105">Syntaxe pro vytváření šablon.</span><span class="sxs-lookup"><span data-stu-id="853b3-105">Syntax for creating templates.</span></span>  
  
- <span data-ttu-id="853b3-106">Vytváření instanci identifikátorů `UriTemplate` <xref:System.UriTemplate.BindByName%2A> URI <xref:System.UriTemplate.BindByPosition%2A>z using a .</span><span class="sxs-lookup"><span data-stu-id="853b3-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
- <span data-ttu-id="853b3-107"><xref:System.UriTemplateTable.Match%2A>, což je inverzní provoz `BindByName` a `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="853b3-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="853b3-108">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="853b3-108">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="853b3-109">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="853b3-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="853b3-110">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="853b3-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="853b3-111">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="853b3-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="853b3-112">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="853b3-112">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="853b3-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="853b3-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="853b3-114">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="853b3-114">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="853b3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="853b3-115">See also</span></span>

- [<span data-ttu-id="853b3-116">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="853b3-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="853b3-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="853b3-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
