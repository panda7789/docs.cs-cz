---
title: Vytvoření nároku a hodnoty prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: cfa697023ca9d4c0b6f43c90c382816993dccc5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488049"
---
# <a name="claim-creation-and-resource-values"></a>Vytvoření nároku a hodnoty prostředků
<xref:System.IdentityModel.Claims.Claim> Třída poskytuje několik metod, vytváření instancí předdefinované typy deklarací identity. Z těchto metod následující provést žádné sémantického nebo formátu kontrola na zadaný prostředek:  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nekontroluje délku nebo obsah pole bajtů)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nekontroluje délku nebo obsah pole bajtů)  
  
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
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
