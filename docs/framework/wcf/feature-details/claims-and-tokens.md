---
title: Deklarace a tokeny
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 6d148bca56cfa4e28c2d3e6c0d9fcb564861a7cd
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663462"
---
# <a name="claims-and-tokens"></a>Deklarace a tokeny

Toto téma popisuje různé typy deklarací identity, které Windows Communication Foundation (WCF) vytvoří z výchozí tokeny, které podporuje.

Deklarace identity pověření klienta můžete prozkoumat pomocí <xref:System.IdentityModel.Claims.ClaimSet> a <xref:System.IdentityModel.Claims.Claim> třídy. `ClaimSet` Obsahuje kolekci `Claim` objekty. Každý `Claim` má následující důležité členy:

- <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> Vrátí vlastnost identifikátor URI (Uniform Resource), který určuje typ deklarace identity prováděné. Typ deklarace identity může být například kryptografického otisku certifikátu, ve kterém je případ identifikátoru URI `http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`.

- <xref:System.IdentityModel.Claims.Claim.Right%2A> Vlastnost vrací identifikátor URI, který určuje vpravo od deklarace identity. Předdefinovaná práva, které se nacházejí v <xref:System.IdentityModel.Claims.Rights> třídy (<xref:System.IdentityModel.Claims.Rights.Identity%2A>, <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>).

- <xref:System.IdentityModel.Claims.Claim.Resource%2A> Vrátí vlastnost prostředku přidružený k deklaraci.

Každý <xref:System.IdentityModel.Claims.ClaimSet> má také <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> vlastnost, která představuje <xref:System.IdentityModel.Claims.ClaimSet> z `Issuer`.

## <a name="windows-accounts"></a>Účty Windows

Pokud pověření klienta mapuje na uživatelský účet Windows, výsledná <xref:System.IdentityModel.Claims.ClaimSet> má následující hodnoty:

- `Issuer` Je hodnoty vrácené statickou vlastnost Windows <xref:System.IdentityModel.Claims.ClaimSet> třídy.

- Deklarace identity v kolekci jsou:

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnota identifikátoru zabezpečení (SID), <xref:System.IdentityModel.Claims.Claim.Right%2A> hodnotou vlastnosti `Identity`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> , který vrací aktuální hodnotu SID. Identifikátor SID je jedinečná hodnota pro každého uživatele problémy s řadičem domény. Identifikátor SID se používá k identifikaci uživatelů v interakce s zabezpečení Windows.

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> hodnotou identifikátoru SID, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> hodnoty SID.

  - A <xref:System.IdentityModel.Claims.Claim> s <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `PossessProperty` a <xref:System.IdentityModel.Claims.Claim.Resource%2A> řetězce obsahující uživatelské jméno (například "MYMACHINE\Bob").

  - Deklarace identifikátoru SID další s <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> pro různé skupiny tento uživatel patří.

## <a name="certificates"></a>Certifikáty

Pokud pověření klienta je certifikát, výsledná <xref:System.IdentityModel.Claims.ClaimSet> má následující hodnoty:

- Samostatně vydané certifikáty `Issuer` je <xref:System.IdentityModel.Claims.ClaimSet> samotný. <xref:System.IdentityModel.Claims.ClaimSet> Vrátí <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> z <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>, <xref:System.IdentityModel.Claims.Claim.Right%2A> z `Identity`a <xref:System.IdentityModel.Claims.Claim.Resource%2A> hodnotu <xref:System.Byte> pole obsahující kryptografický otisk certifikátu.

- Pro certifikát vydaný certifikační autoritou, že vystavitel je `ClaimSet` představující certifikát certifikační autority.

- `Claims` v kolekci patří:

  - A `Claim` s `ClaimType` otisk, `Right` z PossessProperty a `Resource` , který je bajtové pole obsahující kryptografický otisk certifikátu

  - Další deklarace identity PossessProperty různých typů, včetně X500DistinguishedName, Dns, název, hlavní název uživatele a Rsa, představují různé vlastnosti certifikátu. Prostředek pro deklarace identity Rsa je veřejného klíče přidruženého k certifikátu. **Poznámka** kde typu pověření klienta je certifikát, který se mapuje Windows služby účtu, dva `ClaimSet` objekty jsou generovány. První obsahuje všechny deklarace identity související s účtem Windows a druhý obsahuje všechny deklarace identity související s certifikátem.

## <a name="user-namepassword"></a>Uživatelské jméno/heslo

Kde se přihlašovací údaje klienta jméno/heslo uživatele (nebo ekvivalentní), který nemapuje na účet Windows, výsledná `ClaimSet` vydává statické <xref:System.IdentityModel.Claims.ClaimSet.System%2A> vlastnost `ClaimSet` třídy. `ClaimSet` Obsahuje `Identity` deklarace typu <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> jejichž prostředek je uživatelské jméno klienta poskytuje. Má odpovídající deklarace identity `Right` z `PossessProperty`.

## <a name="rsa-keys"></a>Klíče RSA

Tam, kde se používá klíč RSA nesouvisí s certifikátem, výsledná `ClaimSet` svým vydání a obsahuje `Identity` deklarace typu <xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A> jejichž prostředek je klíče RSA. Má odpovídající deklarace identity `Right` z `PossessProperty`.

## <a name="saml"></a>SAML

Pokud klient se ověří pomocí tokenu zabezpečení kontrolní výrazy SAML (Markup Language), výsledná `ClaimSet` vystaví služba entity, který podepsal token SAML, často certifikát služby tokenů zabezpečení (STS), která vydala tokenu SAML. `ClaimSet` Obsahuje různé deklarace identity, jak se nachází v tokenu SAML. Pokud obsahuje SAML token `SamlSubject` s non -`null` název, pak `Identity` deklarace identity s typem <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> a typu prostředku <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> jsou vytvořeny.

## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>Deklarace identity a ServiceSecurityContext.IsAnonymous

Pokud žádná z `ClaimSet` objekty vyplývající z přihlašovacích údajů klienta obsahují deklaraci identity `Right` z `Identity,` pak bude <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vrátí vlastnost `true`. Pokud takové deklarace jsou k dispozici, `IsAnonymous` vrátí vlastnost `false`.

## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
