---
title: Integrace jazyka AJAX a podpora formátu JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: b2bcd1a677f4f2e329422abe202d4b365ad8dc28
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116644"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="765b7-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="765b7-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="765b7-103">Podpora Windows Communication Foundation (WCF) pro ASP.NET Asynchronous JavaScript a XML (AJAX) a formát dat JavaScript Object Notation (JSON) umožňují službám WCF vystavovat operace klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="765b7-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="765b7-104">Klienti AJAX jsou webové stránky spouštějící kód JavaScriptu a získávají přístup k těmto službám WCF pomocí požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="765b7-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="765b7-105">Témata v této části poskytují informace o této podpoře a o tom, jak je implementovat.</span><span class="sxs-lookup"><span data-stu-id="765b7-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="765b7-106">Další informace o ASP.NET AJAX a jeho integraci s ASP.NET 2,0 naleznete v tématu [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="765b7-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="765b7-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="765b7-107">In This Section</span></span>  
 [<span data-ttu-id="765b7-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="765b7-108">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="765b7-109">Popisuje, jak může být služba WCF vystavena klientům AJAX přidáním příslušného koncového bodu AJAX buď prostřednictvím konfigurace, nebo pomocí objektu pro hostování služby přizpůsobeného pro vygenerování hostitele služby, který automaticky konfiguruje koncový bod AJAX.</span><span class="sxs-lookup"><span data-stu-id="765b7-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="765b7-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="765b7-110">Creating WCF AJAX Services without ASP.NET</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="765b7-111">Popisuje, jak vytvořit službu WCF bez použití ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="765b7-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="765b7-112">Podpora JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="765b7-112">Support for JSON and Other Data Transfer Formats</span></span>](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="765b7-113">Popisuje podporu formátu JSON, který se obvykle používá (místo XML) pro zasílání zpráv se službami ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="765b7-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="765b7-114">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="765b7-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="765b7-115">Popisuje, jak migrovat webovou službu ASP.NET s podporou AJAX na webovou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="765b7-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="765b7-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="765b7-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="765b7-117">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="765b7-117">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
