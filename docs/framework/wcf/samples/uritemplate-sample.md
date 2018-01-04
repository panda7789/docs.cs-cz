---
title: "Ukázka UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 035167cfbaf35720a6e172288ffa2941ee4537a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="uritemplate-sample"></a><span data-ttu-id="cc3b0-102">Ukázka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cc3b0-102">UriTemplate Sample</span></span>
<span data-ttu-id="cc3b0-103"><xref:System.UriTemplate> Třída poskytuje metody pro práci se sadami identifikátory URI, které sdílejí společné struktury.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-103">The <xref:System.UriTemplate> class provides methods for working with sets of URIs that share a common structure.</span></span> <span data-ttu-id="cc3b0-104">Tento příklad znázorňuje následující klíčové koncepty týkající se `UriTemplate`:</span><span class="sxs-lookup"><span data-stu-id="cc3b0-104">This sample demonstrates the following key concepts relating to `UriTemplate`:</span></span>  
  
-   <span data-ttu-id="cc3b0-105">Syntaxe pro vytváření šablon.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-105">Syntax for creating templates.</span></span>  
  
-   <span data-ttu-id="cc3b0-106">Vytváření instancí identifikátory URI z `UriTemplate` pomocí <xref:System.UriTemplate.BindByName%2A> a <xref:System.UriTemplate.BindByPosition%2A>.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-106">Instantiating URIs from a `UriTemplate` using <xref:System.UriTemplate.BindByName%2A> and <xref:System.UriTemplate.BindByPosition%2A>.</span></span>  
  
-   <span data-ttu-id="cc3b0-107"><xref:System.UriTemplateTable.Match%2A>, což je inverzní operace `BindByName` a `BindByPosition`.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-107"><xref:System.UriTemplateTable.Match%2A>, which is the inverse operation of `BindByName` and `BindByPosition`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cc3b0-108">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="cc3b0-108">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cc3b0-109">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc3b0-109">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="cc3b0-110">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cc3b0-110">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cc3b0-111">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-111">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cc3b0-112">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cc3b0-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cc3b0-113">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc3b0-114">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cc3b0-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a><span data-ttu-id="cc3b0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc3b0-115">See Also</span></span>  
 [<span data-ttu-id="cc3b0-116">Tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cc3b0-116">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="cc3b0-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="cc3b0-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
