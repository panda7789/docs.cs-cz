---
title: Integrace jazyka AJAX a podpora formátu JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 3054c3c6faa8dfe621c706d8df031c23d497da0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576509"
---
# <a name="ajax-integration-and-json-support"></a><span data-ttu-id="2ae07-102">Integrace jazyka AJAX a podpora formátu JSON</span><span class="sxs-lookup"><span data-stu-id="2ae07-102">AJAX Integration and JSON Support</span></span>
<span data-ttu-id="2ae07-103">Podpora Windows Communication Foundation (WCF) pro ASP.NET Asynchronous JavaScript a XML (AJAX) a formát dat JavaScript Object Notation (JSON) umožňují službám WCF vystavovat operace klientům AJAX.</span><span class="sxs-lookup"><span data-stu-id="2ae07-103">The Windows Communication Foundation (WCF) support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format allow WCF services to expose operations to AJAX clients.</span></span> <span data-ttu-id="2ae07-104">Klienti AJAX jsou webové stránky spouštějící kód JavaScriptu a získávají přístup k těmto službám WCF pomocí požadavků HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ae07-104">AJAX clients are Web pages running JavaScript code and accessing these WCF services using HTTP requests.</span></span> <span data-ttu-id="2ae07-105">Témata v této části poskytují informace o této podpoře a o tom, jak je implementovat.</span><span class="sxs-lookup"><span data-stu-id="2ae07-105">The topics in this section provide information about this support and about how to implement it.</span></span>  
  
 <span data-ttu-id="2ae07-106">Další informace o ASP.NET AJAX a jeho integraci s ASP.NET 2,0 naleznete v tématu [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2ae07-106">For more information about ASP.NET AJAX and its integration with ASP.NET 2.0, see [ASP.NET AJAX Overview](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ae07-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2ae07-107">In This Section</span></span>  
 [<span data-ttu-id="2ae07-108">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="2ae07-108">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)  
 <span data-ttu-id="2ae07-109">Popisuje, jak může být služba WCF vystavena klientům AJAX přidáním příslušného koncového bodu AJAX buď prostřednictvím konfigurace, nebo pomocí objektu pro hostování služby přizpůsobeného pro vygenerování hostitele služby, který automaticky konfiguruje koncový bod AJAX.</span><span class="sxs-lookup"><span data-stu-id="2ae07-109">Describes how a WCF service can be exposed to AJAX clients by adding the appropriate AJAX endpoint either through configuration or by using a service host factory customized to generate a service host that configures the AJAX endpoint automatically.</span></span>  
  
 [<span data-ttu-id="2ae07-110">Vytváření služeb WCF AJAX bez ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2ae07-110">Creating WCF AJAX Services without ASP.NET</span></span>](creating-wcf-ajax-services-without-aspnet.md)  
 <span data-ttu-id="2ae07-111">Popisuje, jak vytvořit službu WCF bez použití ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2ae07-111">Describes how to create a WCF service without using ASP.NET.</span></span>  
  
 [<span data-ttu-id="2ae07-112">Podpora formátu JSON a dalších formátů přenosu dat</span><span class="sxs-lookup"><span data-stu-id="2ae07-112">Support for JSON and Other Data Transfer Formats</span></span>](support-for-json-and-other-data-transfer-formats.md)  
 <span data-ttu-id="2ae07-113">Popisuje podporu formátu JSON, který se obvykle používá (místo XML) pro zasílání zpráv se službami ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="2ae07-113">Describes the support of the JSON format typically used (instead of XML) for messaging with ASP.NET AJAX services.</span></span>  
  
 [<span data-ttu-id="2ae07-114">Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF</span><span class="sxs-lookup"><span data-stu-id="2ae07-114">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 <span data-ttu-id="2ae07-115">Popisuje, jak migrovat webovou službu ASP.NET s podporou AJAX na webovou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="2ae07-115">Describes how to migrate an AJAX-enabled ASP.NET Web service to a WCF Web service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae07-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ae07-116">See also</span></span>

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [<span data-ttu-id="2ae07-117">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="2ae07-117">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
