---
title: "Ukázková tabulka UriTemplate"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c4561590228531066014e69c03fcef0a6142cd70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="106e9-102">Ukázková tabulka UriTemplate</span><span class="sxs-lookup"><span data-stu-id="106e9-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="106e9-103"><xref:System.UriTemplateTable> Třída poskytuje strukturu asociativní tabulky jako slovník pro práci s sadu `UriTemplate` instance.</span><span class="sxs-lookup"><span data-stu-id="106e9-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="106e9-104">Konkrétní identifikátory Uniform Resource (Identifier) je možné porovnávat efektivně proti všechny šablony v tabulce a dá se načíst data přidružená k šabloně odpovídající.</span><span class="sxs-lookup"><span data-stu-id="106e9-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="106e9-105">Tento příklad znázorňuje následující klíčové koncepty související s `UriTemplateTable` třídy:</span><span class="sxs-lookup"><span data-stu-id="106e9-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
-   <span data-ttu-id="106e9-106">Syntaxe pro vytváření instancí `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="106e9-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
-   <span data-ttu-id="106e9-107">Sestavování `UriTemplateTable` s sada párů klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="106e9-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
-   <span data-ttu-id="106e9-108">Odpovídající kandidátem URI před použitím tabulky <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="106e9-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="106e9-109">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="106e9-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="106e9-110">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="106e9-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="106e9-111">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="106e9-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="106e9-112">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="106e9-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="106e9-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="106e9-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="106e9-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="106e9-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="106e9-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="106e9-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="106e9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="106e9-116">See Also</span></span>  
 [<span data-ttu-id="106e9-117">Dispečer tabulky UriTemplate</span><span class="sxs-lookup"><span data-stu-id="106e9-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)  
 [<span data-ttu-id="106e9-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="106e9-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
