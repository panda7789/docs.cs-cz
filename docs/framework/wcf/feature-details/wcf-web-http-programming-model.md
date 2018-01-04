---
title: "Model programování webových služeb HTTP WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f008cfe874ae9e38a71eb3cf5d6b2ed4e6cbdf7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="d880e-102">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="d880e-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Model programování webových protokolu HTTP umožňuje vývojářům vystavit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby operace do koncových bodů protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d880e-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="d880e-104">Témata v této části Zkontrolujte funkci podrobně.</span><span class="sxs-lookup"><span data-stu-id="d880e-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d880e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d880e-105">In This Section</span></span>  
 [<span data-ttu-id="d880e-106">Přehled programovacího modelu webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="d880e-107">Obsahuje přehled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Model programování webových HTTP.</span><span class="sxs-lookup"><span data-stu-id="d880e-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="d880e-108">Programovací objektový model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="d880e-109">Popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Model programování webových HTTP a jak to funguje.</span><span class="sxs-lookup"><span data-stu-id="d880e-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="d880e-110">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="d880e-111">Popisuje, jak napsat základní služby, která zveřejňuje koncový bod-protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d880e-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="d880e-112">Postupy: Zveřejnění kontraktu klientům SOAP a webovým klientům</span><span class="sxs-lookup"><span data-stu-id="d880e-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="d880e-113">Popisuje, jak napsat základní služby, která zveřejňuje stejné smlouvy protokolu SOAP a klienti protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d880e-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="d880e-114">UriTemplate a UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d880e-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="d880e-115">Popisuje, jak řídit identifikátory URI pomocí <xref:System.UriTemplate> a <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="d880e-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="d880e-116">Podpora ukládání dat do mezipaměti pro webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="d880e-117">Popisuje, jak k určení chování ukládání do mezipaměti pro službu WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="d880e-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="d880e-118">Formátování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="d880e-119">Popisuje, jak určit formát odpovědi ze služby WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="d880e-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="d880e-120">Zpracování chyb webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="d880e-121">Popisuje, jak vracet chyby pro klienty webového WCF včetně stavové kódy HTTP a další chybové uživatelská data.</span><span class="sxs-lookup"><span data-stu-id="d880e-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="d880e-122">Volání služby typu REST ze služby WCF</span><span class="sxs-lookup"><span data-stu-id="d880e-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="d880e-123">Popisuje způsob volání služby stylu REST z uvnitř služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d880e-123">Describes how to call a REST-style service from inside a WCF service.</span></span>
