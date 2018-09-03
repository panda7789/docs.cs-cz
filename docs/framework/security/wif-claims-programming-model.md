---
title: Technologie WIF deklarací programovací Model
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e70958ab20ff70462e7301630b36db3df79fd13e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43479903"
---
# <a name="wif-claims-programming-model"></a>Technologie WIF deklarací programovací Model
ASP.NET a služby Windows Communication Foundation (WCF) obvykle vývojáři IIdentity a IPrincipal rozhraní pro práci s informací o identitě uživatele. V rozhraní .NET 4.5 Windows Identity Foundation (WIF) byla integrována tak, že deklarace identity jsou teď vždy k dispozici pro všechny instanční objekt, jak je znázorněno v následujícím diagramu:  
  
 ![Technologie WIF deklarací programovací Model](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 V rozhraní .NET 4.5 System.Security.Claims obsahuje nové třídy ClaimsPrincipal a ClaimsIdentity (viz diagram výše). Všechny objekty zabezpečení v rozhraní .NET jsou nyní odvozeny z objektu ClaimsPrincipal. Všechny třídy integrované identita, jako je FormsIdentity pro ASP.NET a nyní WindowsIdentity odvozovat ClaimsIdentity. Podobně všechny předdefinované instančního objektu třídy jako objektů GenericPrincipal a WindowsPrincipal odvozovat z objektu ClaimsPrincipal.  
  
 Deklarace identity představuje <xref:System.Security.Claims.Claim> třídy. Tato třída obsahuje následující důležité vlastnosti:  
  
-   <xref:System.Security.Claims.Claim.Type%2A> představuje typ deklarace identity a je obvykle identifikátor URI. Například, deklarace identity e-mailová adresa je vyjádřena jako `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.  
  
-   <xref:System.Security.Claims.Claim.Value%2A> obsahuje hodnotu deklarace identity, je vyjádřena jako řetězec. Například e-mailová adresa může být reprezentován jako "someone@contoso.com".  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A> představuje typ hodnoty deklarace identity a je obvykle identifikátor URI. Například typ string je vyjádřena jako `http://www.w3.org/2001/XMLSchema#string`. Typ hodnoty musí být QName podle schématu XML. Hodnota musí být ve formátu `namespace#format` k povolení technologie WIF do výstupního platnou hodnotu QName. Pokud obor názvů není dobře definovaný obor názvů, vygenerovaný kód XML nelze pravděpodobně schématu ověřit, protože nebude publikovaného souboru XSD pro tento obor názvů. Výchozí typ hodnoty je `http://www.w3.org/2001/XMLSchema#string`. Podrobnosti najdete na [ http://www.w3.org/2001/XMLSchema ](https://go.microsoft.com/fwlink/?LinkId=209155) pro dobře známou hodnotu typy, které lze bezpečně použít.  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A> je identifikátor službu tokenů zabezpečení (STS), která vydala deklarace identity. To může být reprezentován jako adresu URL služby STS nebo název, který představuje službu STS, jako například `https://sts1.contoso.com/sts`.  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A> je identifikátor služby tokenů zabezpečení, které původně vystavil deklarace identity, bez ohledu na to, kolik tokenů zabezpečení jsou v řetězci. Stejně jako je reprezentováno <xref:System.Security.Claims.Claim.Issuer%2A>.  
  
-   <xref:System.Security.Claims.Claim.Subject%2A> je předmět, jehož identita je zkoumají. Obsahuje hlavičku <xref:System.Security.Claims.ClaimsIdentity>.  
  
-   <xref:System.Security.Claims.Claim.Properties%2A> je slovník, který umožňuje vývojářům poskytují data specifická pro aplikaci k převedení na lince společně s dalšími vlastnostmi a lze použít pro vlastní ověřování.  
  
## <a name="identity-delegation"></a>Delegování identity  
 Důležité vlastnosti <xref:System.Security.Claims.ClaimsIdentity> je <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Tato vlastnost umožňuje delegování přihlašovacích údajů v systému vícevrstvou, ve kterém střední vrstvy slouží jako klient aby žádostí pro back-end služby.  
  
### <a name="accessing-claims-through-threadcurrentprincipal"></a>Přístup k deklarací vlastnost Thread.CurrentPrincipal  
 Chcete-li získat přístup k aktuální uživatel sadu deklarací identity v aplikaci předávající strany, použijte `Thread.CurrentPrincipal`.  
  
 Následující příklad kódu ukazuje použití této metody k získání System.Security.Claims.ClaimsIdentity:  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
```  
  
 Další informace naleznete v tématu <xref:System.Security.Claims>.  
  
### <a name="role-claim-type"></a>Deklarace typu role  
 Během konfigurace vaší aplikace předávající strany je nutné určit, jakou roli váš deklarace identity, typu by mělo být. Tento typ deklarace identity používá System.Security.Claims.ClaimsPrincipal.IsInRole(System.String). Výchozí typ deklarace identity je `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.  
  
### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Extrahovaná modulem Windows Identity Foundation z jiné typy tokenů deklarace identity  
 Technologie WIF podporuje několik kombinace ověřovacích mechanismů úprav. V následující tabulce jsou uvedeny deklarace, které technologie WIF extrahuje z jiné typy tokenů.  
  
|Typ tokenu|Generované deklarace identity|Mapu, aby Windows přístupový Token|  
|-|-|-|  
|SAML 1.1|1.  All claims from System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope).<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Deklarace identity, který obsahuje XML serializaci klíč potvrzení, pokud token, který obsahuje token důkazu.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Deklarace identity z elementu vystavitele.<br />4.  AuthenticationMethod a AuthenticationInstant deklarací identity, pokud token, který obsahuje příkaz ověřování.|Kromě deklarace uvedené v "SAML 1.1", s výjimkou deklarací identity typu `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, přidá se deklarace identity a identity budou mít stejné WindowsClaimsIdentity související s ověřováním Windows.|  
|PROTOKOL SAML 2.0|Stejné jako "SAML 1.1".|Stejné jako "SAML 1.1 namapovaných na účet Windows".|  
|X509|1.  Deklarace identity s X500 rozlišující název, název_e-mailu, dnsName, SimpleName, UpnName, UrlName, kryptografický otisk, RsaKey (to může být extrahována pomocí metody RSACryptoServiceProvider.ExportParameters z vlastnosti X509Certificate2.PublicKey.Key), DsaKey () To může být extrahována pomocí metody DSACryptoServiceProvider.ExportParameters z vlastnosti X509Certificate2.PublicKey.Key), z X509 SerialNumber vlastnosti certifikátu.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. AuthenticationInstant deklarace identity s hodnotou času, kdy byl certifikát ověřen ve formátu data a času XmlSchema.|1.  Použije název plně kvalifikované domény účtu Windows, jako `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` hodnoty deklarace identity. .<br />2.  Deklarace identity z X509 certifikát není namapován na Windows a deklarace identity z účtu systému windows získat pomocí mapování certifikátu Windows.|  
|HLAVNÍ NÁZEV UŽIVATELE|1.  Deklarace identity jsou podobně jako deklarace identity v části ověřování Windows.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. AuthenticationInstant deklarace identity s hodnotou času, kdy byla ověřena heslo ve formátu data a času XmlSchema.||  
|Windows (Kerberos nebo NTLM)|1.  Deklarace identity generují z přístupového tokenu, jako: PrimarySID DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, GroupSID, DenyOnlySID a název<br />2.  AuthenticationMethod s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. AuthenticationInstant hodnotu čas, kdy Windows přístupový token byl vytvořen ve formátu data a času XMLSchema.||  
|Pár klíče RSA|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` Deklarace identity s hodnotou RSAKeyValue.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. AuthenticationInstant deklarace identity s hodnotou času, kdy došlo k ověření klíče RSA (to znamená, podpis se neověřuje) ve formátu data a času XMLSchema.||  
  
|Typ ověřování|Identifikátor URI, protože ho v "AuthenticationMethod" deklarace identity|  
|-|-|  
|Heslo|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Protokol Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Tento parametr zadán|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|
