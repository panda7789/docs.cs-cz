---
title: "Integrace jazyka AJAX a podpora formátu JSON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98efc62a133b86ab71e34671bc6385a5a94897ea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="def32-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="def32-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="def32-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Podporu pro ASP.NET asynchronní JavaScript a XML (AJAX) a data formátu JavaScript Object Notation (JSON) umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby vystavit operations klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="def32-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span> <span data-ttu-id="def32-104">Klienti AJAX jsou webové stránky spuštění kódu JavaScript a přístup k tyto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby používající požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="def32-104">AJAX clients are Web pages running JavaScript code and accessing these [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services using HTTP requests.</span></span> <span data-ttu-id="def32-105">Témata v této části poskytují informace o tuto podporu a o tom, jak ho implementovat.</span><span class="sxs-lookup"><span data-stu-id="def32-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="def32-106">Technologie ASP.NET AJAX a její integrace s prostředím ASP.NET 2.0, najdete v části [Přehled technologie ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="def32-106"> ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="def32-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="def32-107">In This Section</span></span>  
 [<span data-ttu-id="def32-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="def32-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="def32-109">Popisuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby mohou být zpřístupněny Klienti AJAX tak, že přidáte příslušné koncového bodu AJAX buď prostřednictvím konfigurace nebo pomocí vytváření hostitele služby přizpůsobit tak, aby generovat hostitele služby, který automaticky nakonfiguruje koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="def32-109">Describes how an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="def32-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="def32-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="def32-111">Popisuje postup vytvoření [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] službu bez použití technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="def32-111">Describes how to create an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="def32-112">Podpora formátu JSON a další Data formátů přenosu</span><span class="sxs-lookup"><span data-stu-id="def32-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="def32-113">Popisuje podporu formátu JSON, který je obvykle používá (namísto XML) pro zasílání zpráv pomocí prvku ASP.NET AJAX služby.</span><span class="sxs-lookup"><span data-stu-id="def32-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="def32-114">Postupy: migrace technologie AJAX webových služeb ASP.NET na WCF</span><span class="sxs-lookup"><span data-stu-id="def32-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="def32-115">Popisuje, jak migrovat služby technologie AJAX technologie ASP.NET můžete [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby.</span><span class="sxs-lookup"><span data-stu-id="def32-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def32-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="def32-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="def32-117">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="def32-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
