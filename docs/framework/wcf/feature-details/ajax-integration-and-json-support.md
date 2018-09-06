---
title: Integrace jazyka AJAX a podpora formátu JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: bcf1cab9386d9d9503af6258c1bb39f8744c073b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787698"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="38d46-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="38d46-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="38d46-103">Podpora Windows Communication Foundation (WCF) asynchronní jazyka JavaScript technologie ASP.NET a XML (AJAX) a formátu dat JavaScript Object Notation (JSON) povolte službám WCF vystavit operace klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="38d46-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="38d46-104">Klienti AJAX jsou webové stránky spuštěním kódu jazyka JavaScript a přístup k těchto služeb WCF pomocí požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="38d46-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="38d46-105">Témata v této části poskytují informace o zprostředkovateli zabezpečení Schannel a způsobu jeho implementace.</span><span class="sxs-lookup"><span data-stu-id="38d46-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="38d46-106">Další informace o ASP.NET AJAX a její integrace s prostředím ASP.NET 2.0 najdete v tématu [Přehled technologie ASP.NET AJAX](https://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="38d46-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38d46-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="38d46-107">In This Section</span></span>  
 [<span data-ttu-id="38d46-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="38d46-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="38d46-109">Popisuje, jak můžou být služby WCF zveřejněné klientům AJAX tak, že přidáte na příslušný koncový bod AJAX buď prostřednictvím konfigurace nebo pomocí vytváření hostitele služby přizpůsobit tak, aby generovat hostitele služby, který automaticky nakonfiguruje koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="38d46-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="38d46-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="38d46-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="38d46-111">Popisuje postup vytvoření služby WCF bez použití technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="38d46-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="38d46-112">Podpora JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="38d46-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="38d46-113">Popisuje podporu formátu JSON (namísto XML) obvykle používají pro zasílání zpráv pomocí služby technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="38d46-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="38d46-114">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="38d46-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="38d46-115">Popisuje, jak migrovat s povoleným AJAX technologie ASP.NET webové služby WCF Web service.</span><span class="sxs-lookup"><span data-stu-id="38d46-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d46-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="38d46-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="38d46-117">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="38d46-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
