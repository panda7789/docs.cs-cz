---
title: "Nasazení projektu knihovny WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbddd99125e8615640ca39d091e92cdde87c9faf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-a-wcf-library-project"></a><span data-ttu-id="25693-102">Nasazení projektu knihovny WCF</span><span class="sxs-lookup"><span data-stu-id="25693-102">Deploying a WCF Library Project</span></span>
<span data-ttu-id="25693-103">Toto téma popisuje, jak můžete nasadit [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] projektu knihovny služby.</span><span class="sxs-lookup"><span data-stu-id="25693-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Library Project.</span></span>  
  
## <a name="deploying-a-wcf-service-library"></a><span data-ttu-id="25693-104">Nasazení knihovny služby WCF</span><span class="sxs-lookup"><span data-stu-id="25693-104">Deploying a WCF Service Library</span></span>  
 <span data-ttu-id="25693-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby je dynamická knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="25693-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library is a dynamic-link library (DLL).</span></span> <span data-ttu-id="25693-106">Jako takový ho nelze provést na svou vlastní.</span><span class="sxs-lookup"><span data-stu-id="25693-106">As such, it cannot be executed on its own.</span></span> <span data-ttu-id="25693-107">Musí být nasazeny do hostitelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="25693-107">It needs to be deployed into a hosting environment.</span></span> <span data-ttu-id="25693-108">Další informace o tomto procesu najdete v tématu [hostitelský a využívání služby WCF](http://go.microsoft.com/fwlink/?LinkId=99932).</span><span class="sxs-lookup"><span data-stu-id="25693-108">For more information about this process, see [Hosting and Consuming WCF Services](http://go.microsoft.com/fwlink/?LinkId=99932).</span></span>  
  
 <span data-ttu-id="25693-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby se dá nasadit jako libovolný jiný [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="25693-109">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library can be deployed like any other [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="25693-110">Ale pozor který [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje konfiguraci pro knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="25693-110">However, be aware that [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support configuration for DLLs.</span></span> <span data-ttu-id="25693-111"><xref:System.Configuration>podporuje jeden soubor konfigurace pro doménu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="25693-111"><xref:System.Configuration> supports one configuration file per app-domain.</span></span> <span data-ttu-id="25693-112">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu knihovny služby nebude toto omezení tím, že poskytuje soubor App.config pro knihovnu během vývoje.</span><span class="sxs-lookup"><span data-stu-id="25693-112">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service library project alleviates this limitation by providing an App.config file for the library during development.</span></span> <span data-ttu-id="25693-113">Soubor App.config se však nerozpoznal po nasazení.</span><span class="sxs-lookup"><span data-stu-id="25693-113">However, the App.config file is not recognized after deployment.</span></span>  
  
 <span data-ttu-id="25693-114">Je nutné přesunout konfigurace kódu do konfiguračního souboru rozpoznáno hostitelského prostředí.</span><span class="sxs-lookup"><span data-stu-id="25693-114">You have to move your configuration code into the configuration file recognized by your hosting environment.</span></span> <span data-ttu-id="25693-115">Pro vlastní hostování, měli byste zkopírovat obsah souboru App.config do souboru App.config hostování spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="25693-115">For self-hosting, you should copy the contents of the App.config file into the App.config file of the hosting executable.</span></span> <span data-ttu-id="25693-116">Pokud použijete k hostování služby IIS, měli byste zkopírovat obsah souboru App.config v souboru Web.config virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="25693-116">If you use IIS to host your service, you should copy the contents of the App.config file into the Web.config file of the virtual directory.</span></span>
