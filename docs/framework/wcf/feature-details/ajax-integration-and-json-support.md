---
title: "Integrace jazyka AJAX a podpora formátu JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cd5c84250349f4adaaac68a302d771280328a4e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="45716-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="45716-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="45716-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Podporu pro ASP.NET asynchronní JavaScript a XML (AJAX) a data formátu JavaScript Object Notation (JSON) umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby vystavit operations klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="45716-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="45716-104">Klienti AJAX jsou webové stránky spuštění kódu JavaScript a přístup k tyto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby používající požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="45716-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="45716-105">Témata v této části poskytují informace o tuto podporu a o tom, jak ho implementovat.</span><span class="sxs-lookup"><span data-stu-id="45716-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="45716-106">Technologie ASP.NET AJAX a její integrace s prostředím ASP.NET 2.0, najdete v části [Přehled technologie ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="45716-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45716-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="45716-107">In This Section</span></span>  
 [<span data-ttu-id="45716-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="45716-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="45716-109">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby mohou být zpřístupněny Klienti AJAX tak, že přidáte příslušné koncového bodu AJAX buď prostřednictvím konfigurace nebo pomocí vytváření hostitele služby přizpůsobit tak, aby generovat hostitele služby, který automaticky nakonfiguruje koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="45716-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="45716-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45716-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="45716-111">Popisuje postup vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu bez použití technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="45716-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="45716-112">Podpora JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="45716-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="45716-113">Popisuje podporu formátu JSON, který je obvykle používá (namísto XML) pro zasílání zpráv pomocí prvku ASP.NET AJAX služby.</span><span class="sxs-lookup"><span data-stu-id="45716-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="45716-114">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="45716-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="45716-115">Popisuje, jak migrovat služby technologie AJAX technologie ASP.NET můžete [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby.</span><span class="sxs-lookup"><span data-stu-id="45716-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45716-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="45716-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="45716-117">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="45716-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
