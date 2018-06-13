---
title: Integrace jazyka AJAX a podpora formátu JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 0b392044db3fbc926bf77ac305ece294880216d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488826"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="cdead-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="cdead-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="cdead-103">Podpora Windows Communication Foundation (WCF) pro ASP.NET asynchronní JavaScript a XML (AJAX) a formát JavaScript Object Notation (JSON) dat povolit služby WCF vystavit operations klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="cdead-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="cdead-104">Klienti AJAX jsou webové stránky spuštění kódu JavaScript a přístup k těchto služeb WCF pomocí požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="cdead-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="cdead-105">Témata v této části poskytují informace o tuto podporu a o tom, jak ho implementovat.</span><span class="sxs-lookup"><span data-stu-id="cdead-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="cdead-106">Další informace o prvku ASP.NET AJAX a její integrace s prostředím ASP.NET 2.0, naleznete v části [Přehled technologie ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=96725).</span><span class="sxs-lookup"><span data-stu-id="cdead-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](http://go.microsoft.com/fwlink/?LinkId=96725).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdead-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cdead-107">In This Section</span></span>  
 [<span data-ttu-id="cdead-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="cdead-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="cdead-109">Popisuje, jak mohou být služby WCF zpřístupněny klientům AJAX tak, že přidáte příslušné koncového bodu AJAX buď prostřednictvím konfigurace nebo pomocí objektu factory hostitele služby přizpůsobit tak, aby generovat hostitele služby, který automaticky nakonfiguruje koncového bodu AJAX.</span><span class="sxs-lookup"><span data-stu-id="cdead-109">Describes how an WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="cdead-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="cdead-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="cdead-111">Popisuje postup vytvoření služby WCF bez použití technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cdead-111">Describes how to create an WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="cdead-112">Podpora JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="cdead-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="cdead-113">Popisuje podporu formátu JSON, který je obvykle používá (namísto XML) pro zasílání zpráv pomocí prvku ASP.NET AJAX služby.</span><span class="sxs-lookup"><span data-stu-id="cdead-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="cdead-114">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="cdead-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="cdead-115">Popisuje, jak migrovat podporou AJAXU ASP.NET webové služby WCF webové služby.</span><span class="sxs-lookup"><span data-stu-id="cdead-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdead-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdead-116">See Also</span></span>  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>  
 [<span data-ttu-id="cdead-117">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="cdead-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
