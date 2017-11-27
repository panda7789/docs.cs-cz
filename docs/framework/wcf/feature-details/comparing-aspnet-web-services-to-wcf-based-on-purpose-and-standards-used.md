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
# <a name="comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used"></a>Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů
Webových služeb ASP.NET byla vyvinuta pro vytváření aplikací, které odesílat a přijímat zprávy pomocí objekt přístup protokolu SOAP (Simple) přes HTTP. Struktura zprávy lze definovat pomocí schématu XML a nástroj slouží k usnadnění serializaci zprávy do a z objekty rozhraní .NET Framework. Technologie může automaticky generovat metadata k popisu webové služby v webové služby popis Language (WSDL) a druhý nástroj se poskytuje pro generování klientů pro webové služby ze schématu WSDL.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]je pro povolení aplikací rozhraní .NET Framework pro výměnu zpráv s dalšími subjekty, softwaru. Protokolu SOAP se používá ve výchozím nastavení, ale může být v libovolném formátu zprávy a bude předávat pomocí libovolný protokol pro přenos. Struktura zprávy lze definovat pomocí schématu XML a existují různé možnosti pro serializaci zprávy do a z objekty rozhraní .NET Framework. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]může automaticky generovat metadata k popisu aplikace vytvořené pomocí technologie v jazyce WSDL a také poskytuje nástroje pro generování klientů pro tyto aplikace ze schématu WSDL.  
  
 Standardů podporovaných webových služeb ASP.NET jsou dokumentovány v článku [XML webové služby vytvořené pomocí ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872). Rozšířený seznam standardy nepodporuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou uvedeny v [webové služby protokoly podporované vazbami vzájemné spolupráce System-Provided](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## <a name="see-also"></a>Viz také  
 [Porovnání webových služeb ASP.NET na WCF z hlediska vývojových požadavků](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
