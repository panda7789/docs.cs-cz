---
title: "Formáty metadat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d250b57282d24780dcdd1e045f18d7528bd86a90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="metadata-formats"></a><span data-ttu-id="137d9-102">Formáty metadat</span><span class="sxs-lookup"><span data-stu-id="137d9-102">Metadata Formats</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="137d9-103">podporuje formáty metadat v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="137d9-103"> supports the metadata formats in the following table.</span></span>  
  
## <a name="metadata-specifications-and-usage"></a><span data-ttu-id="137d9-104">Specifikace metadat a využití</span><span class="sxs-lookup"><span data-stu-id="137d9-104">Metadata Specifications and Usage</span></span>  
  
|<span data-ttu-id="137d9-105">Protokol</span><span class="sxs-lookup"><span data-stu-id="137d9-105">Protocol</span></span>|<span data-ttu-id="137d9-106">Specifikace a využití</span><span class="sxs-lookup"><span data-stu-id="137d9-106">Specification and usage</span></span>|  
|--------------|-----------------------------|  
|<span data-ttu-id="137d9-107">WSDL 1.1</span><span class="sxs-lookup"><span data-stu-id="137d9-107">WSDL 1.1</span></span>|[<span data-ttu-id="137d9-108">Web Services Description Language (WSDL) 1.1</span><span class="sxs-lookup"><span data-stu-id="137d9-108">Web Services Description Language (WSDL) 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-109">Webové služby popis Language (WSDL) používá k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="137d9-109"> uses Web Services Description Language (WSDL) to describe services.</span></span>|  
|<span data-ttu-id="137d9-110">XML schéma</span><span class="sxs-lookup"><span data-stu-id="137d9-110">XML Schema</span></span>|<span data-ttu-id="137d9-111">[XML schéma část 2: Datové typy druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94861) a [XML schéma část 1: struktury druhé vydání](http://go.microsoft.com/fwlink/?LinkId=94862)</span><span class="sxs-lookup"><span data-stu-id="137d9-111">[XML Schema Part 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) and [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)</span></span><br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-112">k popisu typy dat používaných v zprávy používá schéma XML.</span><span class="sxs-lookup"><span data-stu-id="137d9-112"> uses the XML Schema to describe data types used in messages.</span></span>|  
|<span data-ttu-id="137d9-113">Zásady WS</span><span class="sxs-lookup"><span data-stu-id="137d9-113">WS Policy</span></span>|[<span data-ttu-id="137d9-114">Webové služby zásady 1.2 - Framework (WS-Policy)</span><span class="sxs-lookup"><span data-stu-id="137d9-114">Web Services Policy 1.2 - Framework (WS-Policy)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [<span data-ttu-id="137d9-115">Webové služby zásady 1.5 – Framework</span><span class="sxs-lookup"><span data-stu-id="137d9-115">Web Services Policy 1.5 - Framework</span></span>](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-116">používá WS-Policy 1.2 nebo 1,5 specifikace s kontrolní výrazy specifické pro doménu k popisu služby požadavky a možnosti.</span><span class="sxs-lookup"><span data-stu-id="137d9-116"> uses the WS-Policy 1.2 or 1.5 specifications with domain-specific assertions to describe service requirements and capabilities.</span></span>|  
|<span data-ttu-id="137d9-117">Zásady WS příloh</span><span class="sxs-lookup"><span data-stu-id="137d9-117">WS Policy Attachments</span></span>|[<span data-ttu-id="137d9-118">Webové služby zásady 1.2 - přílohy (WS-PolicyAttachment)</span><span class="sxs-lookup"><span data-stu-id="137d9-118">Web Services Policy 1.2 - Attachment (WS-PolicyAttachment)</span></span>](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-119">implementuje WS-Policy přílohy připojit výrazy zásad na různé obory ve schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="137d9-119"> implements WS-Policy Attachments to attach policy expressions at various scopes in WSDL.</span></span>|  
|<span data-ttu-id="137d9-120">WS Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="137d9-120">WS Metadata Exchange</span></span>|[<span data-ttu-id="137d9-121">Webové služby Metadata Exchange (WS-MetadataExchange) verze 1.1</span><span class="sxs-lookup"><span data-stu-id="137d9-121">Web Services Metadata Exchange (WS-MetadataExchange) version 1.1</span></span>](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-122">implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.</span><span class="sxs-lookup"><span data-stu-id="137d9-122"> implements WS-MetadataExchange to retrieve XML Schema, WSDL, and WS-Policy.</span></span>|  
|<span data-ttu-id="137d9-123">WS adresování vazby pro WSDL</span><span class="sxs-lookup"><span data-stu-id="137d9-123">WS Addressing Binding for WSDL</span></span>|[<span data-ttu-id="137d9-124">Webové služby adresování 1.0 - vazby WSDL</span><span class="sxs-lookup"><span data-stu-id="137d9-124">Web Services Addressing 1.0 - WSDL Binding</span></span>](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="137d9-125">implementuje WS-Addressing vazba pro WSDL připojit informace o přidělování v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="137d9-125"> implements WS-Addressing Binding for WSDL to attach addressing information in WSDL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="137d9-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="137d9-126">See Also</span></span>  
 [<span data-ttu-id="137d9-127">Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem</span><span class="sxs-lookup"><span data-stu-id="137d9-127">Web Services Protocols Supported by System-Provided Interoperability Bindings</span></span>](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [<span data-ttu-id="137d9-128">WSDL a zásady</span><span class="sxs-lookup"><span data-stu-id="137d9-128">WSDL and Policy</span></span>](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
