---
title: "Vytvoření nároku a hodnoty prostředků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8213931a7509378fde6df19eeb189abd8a81e96
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="claim-creation-and-resource-values"></a>Vytvoření nároku a hodnoty prostředků
<xref:System.IdentityModel.Claims.Claim> Třída poskytuje několik metod, vytváření instancí předdefinované typy deklarací identity. Z těchto metod následující provést žádné sémantického nebo formátu kontrola na zadaný prostředek:  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A>(nekontroluje délku nebo obsah pole bajtů)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A>(nekontroluje délku nebo obsah pole bajtů)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 Potřeba dát pozor při volání metody výše aby prostředek, který předané hodnoty jsou ve správném formátu nebo obsahují správný druh informací (nebo obě).  
  
 Tyto metody přijímají konkrétní typy:  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
