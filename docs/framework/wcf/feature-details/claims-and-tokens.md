---
title: Deklarace a tokeny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b2e571e8526581269cedb65b83c9ea0d8a81e280
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-tokens"></a>Deklarace a tokeny
Toto téma popisuje různé typy deklarací identity, která [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] vytvoří z výchozí tokeny, které podporuje.  
  
 Deklarace identity pověření klienta můžete zkontrolovat pomocí <xref:System.IdentityModel.Claims.ClaimSet> a <xref:System.IdentityModel.Claims.Claim> třídy. `ClaimSet` Obsahuje kolekci `Claim` objekty. Každý `Claim` má následující důležité členy:  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Vlastnost vrací identifikátor URI (Uniform Resource) určující typ deklarace identity prováděné. Typ deklarace identity může být například kryptografický otisk certifikátu, ve kterém jsou rozlišována identifikátor URI http:schemas.microsoft.com/ws/20005/05/identity/claims/thumprint.  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> Vlastnost vrací identifikátor URI, který určuje právo deklarace identity. Předdefinovaná práva, které se nacházejí v <xref:System.IdentityModel.Claims.Rights> – třída (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> Vlastnost vrací prostředků přidružený k deklaraci.  
  
 Každý <xref:System.IdentityModel.Claims.ClaimSet> má také <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> vlastnosti, která představuje <xref:System.IdentityModel.Claims.ClaimSet> z `Issuer`.  
  
## <a name="windows-accounts"></a>Účty v systému Windows  
 Kde pověření klienta mapuje na uživatelský účet systému Windows, výsledná <xref:System.IdentityModel.Claims.ClaimSet> má následující hodnoty:  
  
-   `Issuer` Je hodnoty vrácené statické vlastnosti systému Windows <xref:System.IdentityModel.Claims.ClaimSet> třídy.  
  
-   Jsou deklarace identity v kolekci:  
  
    -   A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnota identifikátoru zabezpečení (SID), <xref:System.IdentityModel.Claims.Claim.Right%2A> hodnota vlastnosti `Identity`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> který vrací aktuální hodnotu SID. Identifikátor SID je jedinečná hodnota vydává řadičem domény pro každého uživatele. Identifikátor SID se používá k identifikaci uživatele v interakce s zabezpečení systému Windows.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnota identifikátoru SID, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> hodnoty SID.  
  
    -   A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty` a <xref:System.IdentityModel.Claims.Claim.Resource%2A> řetězce obsahující uživatelské jméno (například "MYMACHINE\Bob").  
  
    -   Deklarace identifikátoru SID další s <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pro různé skupiny uživatel patří.  
  
## <a name="certificates"></a>Certifikáty  
 Kde pověření klienta je certifikát, výsledná <xref:System.IdentityModel.Claims.ClaimSet> má následující hodnoty:  
  
-   Pro samoobslužné vydané certifikáty `Issuer` je <xref:System.IdentityModel.Claims.ClaimSet> sám sebe. <xref:System.IdentityModel.Claims.ClaimSet> Vrátí <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `Identity`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> hodnoty, který je <xref:System.Byte> pole obsahující kryptografický otisk certifikátu.  
  
-   Pro certifikát vydaný certifikační autority, Vystavitel je `ClaimSet` představující certifikát certifikační autority.  
  
-   `Claims` v kolekci patří:  
  
    -   A `Claim` s `ClaimType` z kryptografický otisk, `Right` z PossessProperty a `Resource` tedy bajtové pole obsahující kryptografický otisk certifikátu  
  
    -   Další deklarace identity PossessProperty různých typů, včetně X500DistinguishedName, Dns, název, Upn a Rsa, představují různé vlastnosti certifikátu. Prostředek pro deklarace identity Rsa je veřejného klíče přidruženého k certifikátu. **Poznámka** kde typu pověření klienta je certifikát, který mapuje službu Windows účet, dva `ClaimSet` objekty jsou generovány. První všechny deklarace identity související s účet systému Windows a druhá obsahuje všechny deklarace identity související s certifikátem.  
  
## <a name="user-namepassword"></a>Uživatelské jméno a heslo  
 Kde pověření klienta je jméno a heslo uživatele (nebo ekvivalentní), není přiřazena k účet systému Windows, výsledná `ClaimSet` vydává statických <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost `ClaimSet` třídy. `ClaimSet` Obsahuje `Identity` deklarace identity typu <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> jejichž prostředek je uživatelské jméno klienta poskytuje. Má odpovídající deklarace identity `Right` z `PossessProperty`.  
  
## <a name="rsa-keys"></a>Klíče RSA  
 Kde se používá klíč RSA není spojený s certifikátem, výsledná `ClaimSet` samoobslužné vydání a obsahuje `Identity` deklarace identity typu <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> jejichž prostředek je klíče RSA. Má odpovídající deklarace identity `Right` z `PossessProperty`.  
  
## <a name="saml"></a>SAML  
 Kde klient se ověří s tokenem zabezpečení kontrolní výrazy Markup Language (SAML), výsledná `ClaimSet` vydává entity, který podepsal token SAML, často certifikát služby tokenů na zabezpečení (STS), která vydala tokenu SAML. `ClaimSet` Obsahuje různé deklarace identity, jak se nachází v tokenu SAML. Pokud obsahuje tokenu SAML `SamlSubject` s jinou hodnotu než`null` název, potom `Identity` deklarace identity s typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> a typ prostředku <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> vytvářejí.  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Deklarace identity a ServiceSecurityContext.IsAnonymous  
 Pokud žádná z `ClaimSet` objekty vyplývající z pověření klienta obsahovat deklaraci identity `Right` z `Identity,` potom <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost vrátí `true`. Pokud jsou přítomny, jednu nebo více těchto deklarací `IsAnonymous` vlastnost vrátí `false`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
