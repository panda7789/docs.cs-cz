---
title: Deklarace a tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: cbc97f2224bce640757e1cef88fe325db477cfd7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587024"
---
# <a name="claims-and-tokens"></a>Deklarace a tokeny

Toto téma popisuje různé typy deklarací identity, které Windows Communication Foundation (WCF) vytvoří z výchozích tokenů, které podporuje.

Můžete kontrolovat deklarace přihlašovacích údajů klienta pomocí <xref:System.IdentityModel.Claims.ClaimSet> <xref:System.IdentityModel.Claims.Claim> tříd a. `ClaimSet`Obsahuje kolekci `Claim` objektů. Každý `Claim` má následující důležité členy:

- <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>Vlastnost vrací identifikátor URI (Uniform Resource Identifier), který určuje typ vytvářené deklarace identity. Typ deklarace identity může být například kryptografický otisk certifikátu. v takovém případě je identifikátor URI `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint` .

- <xref:System.IdentityModel.Claims.Claim.Right%2A>Vlastnost vrací identifikátor URI, který určuje napravo od deklarace identity. Předdefinovaná práva se nacházejí ve <xref:System.IdentityModel.Claims.Rights> třídě ( <xref:System.IdentityModel.Claims.Rights.Identity%2A> , <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> ).

- <xref:System.IdentityModel.Claims.Claim.Resource%2A>Vlastnost vrací prostředek přidružený k deklaraci identity.

Každá <xref:System.IdentityModel.Claims.ClaimSet> z nich má také <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> vlastnost, která představuje <xref:System.IdentityModel.Claims.ClaimSet> z `Issuer` .

## <a name="windows-accounts"></a>Účty systému Windows

V případě, že se pověření klienta mapuje na uživatelský účet systému Windows, má výsledný výsledek <xref:System.IdentityModel.Claims.ClaimSet> následující hodnoty:

- `Issuer`Je hodnota vrácená vlastností static systému Windows <xref:System.IdentityModel.Claims.ClaimSet> třídy.

- Deklarace v kolekci jsou:

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnotou identifikátoru zabezpečení (SID), <xref:System.IdentityModel.Claims.Claim.Right%2A> hodnoty vlastnosti `Identity` a, <xref:System.IdentityModel.Claims.Claim.Resource%2A> která vrací skutečnou hodnotu SID. Identifikátor SID je jedinečná hodnota, kterou řadič domény vydá každému uživateli. Identifikátor SID slouží k identifikaci uživatele v interakcích se zabezpečením systému Windows.

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnotou SID, <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` a a <xref:System.IdentityModel.Claims.Claim.Resource%2A> hodnotou SID.

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> řetězcem, který <xref:System.IdentityModel.Claims.Claim.Right%2A> `PossessProperty` <xref:System.IdentityModel.Claims.Claim.Resource%2A> obsahuje uživatelské jméno (například "MYMACHINE\Bob").

  - Další deklarace SID <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pro různé skupiny, do kterých uživatel patří.

## <a name="certificates"></a>Certifikáty

Pokud je pověření klienta certifikátem, má výsledný výsledek <xref:System.IdentityModel.Claims.ClaimSet> následující hodnoty:

- V případě certifikátů samostatně vydaných `Issuer` je to <xref:System.IdentityModel.Claims.ClaimSet> sám. <xref:System.IdentityModel.Claims.ClaimSet>Vrátí a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A> <xref:System.IdentityModel.Claims.Claim.Right%2A> `Identity` a hodnotu, <xref:System.IdentityModel.Claims.Claim.Resource%2A> která je <xref:System.Byte> pole obsahující kryptografický otisk certifikátu.

- Pro certifikát vydaný certifikační autoritou je Vydavatel `ClaimSet` reprezentující certifikát certifikační autority.

- Do `Claims` kolekce patří:

  - `Claim`S `ClaimType` kryptografickým otiskem, typu `Right` PossessProperty a `Resource` , který je bajtové pole obsahující kryptografický otisk certifikátu.

  - Další PossessProperty deklarace různých typů, včetně X500DistinguishedName, DNS, názvu, UPN a RSA, reprezentují různé vlastnosti certifikátu. Prostředek pro deklaraci RSA je veřejný klíč přidružený k certifikátu. **Poznámka:** Pokud je typ přihlašovacích údajů klienta certifikát, který služba mapuje na účet systému Windows, `ClaimSet` generují se dva objekty. První obsahuje všechny deklarace identity vztahující se k účtu systému Windows a druhý obsahuje všechny deklarace identity související s certifikátem.

## <a name="user-namepassword"></a>Uživatelské jméno a heslo

Kde pověření klienta je uživatelské jméno/heslo (nebo ekvivalentní), které není mapováno na účet systému Windows, výsledek `ClaimSet` je vydaný statickou <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastností `ClaimSet` třídy. `ClaimSet`Obsahuje `Identity` deklaraci identity typu, <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> jejíž prostředek je uživatelské jméno, které poskytuje klient. Odpovídající deklarace identity má `Right` `PossessProperty` .

## <a name="rsa-keys"></a>Klíče RSA

Tam, kde se používá klíč RSA, který není přidružený k certifikátu, je výsledný certifikát `ClaimSet` vystavený svým držitelem a obsahuje `Identity` deklaraci identity typu, <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> jejíž prostředek je klíč RSA. Odpovídající deklarace identity má `Right` `PossessProperty` .

## <a name="saml"></a>SAML

Pokud se klient ověřuje pomocí tokenu SAML (Security Assert Markup Language), výsledek `ClaimSet` je vydaný entitou, která podepsala token SAML, často certifikátem služby tokenu zabezpečení (STS), která vystavila token SAML. `ClaimSet`Obsahuje různé deklarace identity, které se nacházejí v tokenu SAML. Pokud token SAML obsahuje a je typu `SamlSubject` bez `null` názvu, `Identity` vytvoří se deklarace identity s typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> a typem prostředku <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> .

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Deklarace identity a ServiceSecurityContext. Anonymous

Pokud žádný z `ClaimSet` objektů vyplývajících z pověření klienta neobsahuje deklaraci identity s a `Right` , `Identity,` <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vrátí vlastnost hodnotu `true` . Pokud je přítomna jedna nebo více takových deklarací, `IsAnonymous` vrátí vlastnost `false` .

## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Správa deklarací a autorizace s modelem identity](managing-claims-and-authorization-with-the-identity-model.md)
