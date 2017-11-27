---
title: "Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6dc444b8a4c19dbe486eb904e0f054e05f6fe6a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a><span data-ttu-id="67735-102">Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů</span><span class="sxs-lookup"><span data-stu-id="67735-102">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>
<span data-ttu-id="67735-103">Webových služeb ASP.NET byla vyvinuta pro vytváření aplikací, které odesílat a přijímat zprávy pomocí objekt přístup protokolu SOAP (Simple) přes HTTP.</span><span class="sxs-lookup"><span data-stu-id="67735-103">ASP.NET Web services was developed for building applications that send and receive messages by using the Simple Object Access Protocol (SOAP) over HTTP.</span></span> <span data-ttu-id="67735-104">Struktura zprávy lze definovat pomocí schématu XML a nástroj slouží k usnadnění serializaci zprávy do a z objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67735-104">The structure of the messages can be defined using an XML Schema, and a tool is provided to facilitate serializing the messages to and from .NET Framework objects.</span></span> <span data-ttu-id="67735-105">Technologie může automaticky generovat metadata k popisu webové služby v webové služby popis Language (WSDL) a druhý nástroj se poskytuje pro generování klientů pro webové služby ze schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="67735-105">The technology can automatically generate metadata to describe Web services in the Web Services Description Language (WSDL), and a second tool is provided for generating clients for Web services from the WSDL.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="67735-106">je pro povolení aplikací rozhraní .NET Framework pro výměnu zpráv s dalšími subjekty, softwaru.</span><span class="sxs-lookup"><span data-stu-id="67735-106"> is for enabling .NET Framework applications to exchange messages with other software entities.</span></span> <span data-ttu-id="67735-107">Protokolu SOAP se používá ve výchozím nastavení, ale může být v libovolném formátu zprávy a bude předávat pomocí libovolný protokol pro přenos.</span><span class="sxs-lookup"><span data-stu-id="67735-107">SOAP is used by default, but the messages can be in any format, and conveyed by using any transport protocol.</span></span> <span data-ttu-id="67735-108">Struktura zprávy lze definovat pomocí schématu XML a existují různé možnosti pro serializaci zprávy do a z objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67735-108">The structure of the messages can be defined using an XML Schema, and there are various options for serializing the messages to and from .NET Framework objects.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="67735-109">může automaticky generovat metadata k popisu aplikace vytvořené pomocí technologie v jazyce WSDL a také poskytuje nástroje pro generování klientů pro tyto aplikace ze schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="67735-109"> can automatically generate metadata to describe applications built using the technology in WSDL, and it also provides a tool for generating clients for those applications from the WSDL.</span></span>  
  
 <span data-ttu-id="67735-110">Standardů podporovaných webových služeb ASP.NET jsou dokumentovány v článku [XML webové služby vytvořené pomocí ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span><span class="sxs-lookup"><span data-stu-id="67735-110">The standards supported by ASP.NET Web services are documented in [XML Web Services Created Using ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).</span></span> <span data-ttu-id="67735-111">Rozšířený seznam standardy nepodporuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou uvedeny v [webové služby protokoly podporované vazbami vzájemné spolupráce System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="67735-111">The more extensive list of standards supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are listed at [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67735-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="67735-112">See Also</span></span>  
 [<span data-ttu-id="67735-113">Porovnání webových služeb ASP.NET na WCF z hlediska vývojových požadavků</span><span class="sxs-lookup"><span data-stu-id="67735-113">Comparing ASP.NET Web Services to WCF Based on Development</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
