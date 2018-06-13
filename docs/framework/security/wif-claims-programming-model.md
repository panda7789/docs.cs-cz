---
title: Deklarace identity WIF programovací Model
ms.date: 03/30/2017
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 71327fb5a86c30d15ff060eff5cce170695e86a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408964"
---
# <a name="wif-claims-programming-model"></a>Deklarace identity WIF programovací Model
Vývojáři ASP.NET a Windows Communication Foundation (WCF) normálně používat rozhraní identita a IPrincipal pro práci s informací o identitě uživatele. V rozhraní .NET 4.5 Windows Identity Foundation (WIF) je integrována funkce tak, že deklarace identity jsou nyní vždy k dispozici pro všechny hlavní, jak je znázorněno v následujícím diagramu:  
  
 ![WIF deklarací modelu programování](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 V rozhraní .NET 4.5 System.Security.Claims obsahuje nové třídy ClaimsPrincipal a ClaimsIdentity (viz diagramu výše). Všechny objekty zabezpečení v rozhraní .NET teď odvozovat z objektu ClaimsPrincipal. Všechny třídy předdefinované identity, jako je FormsIdentity pro technologii ASP.NET a nyní WindowsIdentity odvozen od ClaimsIdentity. Podobně jako GenericPrincipal a WindowsPrincipal všechny třídy integrované zabezpečení odvozen od objektu ClaimsPrincipal.  
  
 Deklarace identity je reprezentována <xref:System.Security.Claims.Claim> třídy. Tato třída obsahuje následující důležité vlastnosti:  
  
-   <xref:System.Security.Claims.Claim.Type%2A> představuje typ deklarace identity a většinou je to identifikátor URI. Například deklarace identity e-mailová adresa je reprezentován jako `http://schemas.microsoft.com/ws/2008/06/identity/claims/email`.  
  
-   <xref:System.Security.Claims.Claim.Value%2A> obsahuje hodnotu deklarace identity a je reprezentována jako řetězec. Například e-mailová adresa může být reprezentován jako "someone@contoso.com".  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A> představuje typ hodnota deklarace identity a většinou je to identifikátor URI. Například na řetězcový typ. vyjádřené `http://www.w3.org/2001/XMLSchema#string`. Typ hodnoty musí být QName podle schématu XML. Hodnota musí být ve formátu `namespace#format` povolit WIF na platnou hodnotu QName výstup. Pokud obor názvů není dobře definovaný obor názvů, generovaný soubor XML nelze pravděpodobně schématu ověřit, protože nebude publikovaného souboru XSD pro tento obor názvů. Výchozí typ hodnoty je `http://www.w3.org/2001/XMLSchema#string`. Najdete v tématu [ http://www.w3.org/2001/XMLSchema ](http://go.microsoft.com/fwlink/?LinkId=209155) pro typy dobře známou hodnotu, která můžete bezpečně.  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A> je identifikátor služby tokenů na zabezpečení (STS), která vydala deklarace identity. To může být reprezentován jako adresu URL Služba tokenů zabezpečení nebo název, který představuje službu tokenů zabezpečení, například `https://sts1.contoso.com/sts`.  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A> je identifikátor služby tokenů zabezpečení, které původně vystavil deklarací identity, bez ohledu na to, kolik STSs v řetězu. To je reprezentována podobně jako <xref:System.Security.Claims.Claim.Issuer%2A>.  
  
-   <xref:System.Security.Claims.Claim.Subject%2A> je subjektu, jehož identita je právě zkontrolován. Obsahuje hlavičku <xref:System.Security.Claims.ClaimsIdentity>.  
  
-   <xref:System.Security.Claims.Claim.Properties%2A> je slovník, který umožňuje vývojáři zadejte specifické pro aplikaci přenos dat do přenášený společně s dalšími vlastnostmi a lze použít pro vlastní ověřování.  
  
## <a name="identity-delegation"></a>Delegování identity  
 Důležité vlastnost <xref:System.Security.Claims.ClaimsIdentity> je <xref:System.Security.Claims.ClaimsIdentity.Actor%2A>. Tato vlastnost umožňuje delegování pověření ve vícevrstvé systému střední vrstvy funguje jako klient provádět požadavky na back endové službě.  
  
### <a name="accessing-claims-through-threadcurrentprincipal"></a>Přístup k deklarace identity prostřednictvím Thread.CurrentPrincipal  
 Chcete-li získat přístup k aktuální uživatel sadu deklarací identity v aplikaci RP, použijte `Thread.CurrentPrincipal`.  
  
 Následující příklad kódu ukazuje použití tuto metodu za účelem získání System.Security.Claims.ClaimsIdentity:  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
```  
  
 Další informace naleznete v tématu <xref:System.Security.Claims>.  
  
### <a name="role-claim-type"></a>Typ deklarace role  
 Součástí konfigurace aplikace RP je určit, jaké vaše role deklarace identity musí být typu. Tento typ deklarace identity se používá ve System.Security.Claims.ClaimsPrincipal.IsInRole(System.String). Je výchozím typem deklarace identity `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`.  
  
### <a name="claims-extracted-by-windows-identity-foundation-from-different-token-types"></a>Extrahovat pomocí technologie Windows Identity Foundation z tokenu různé typy deklarací identity  
 WIF podporuje několik kombinace ověřovací mechanismy, které mimo pole. Následující tabulka uvádí deklarace identity, které technologii WIF extrahuje z jiné typy tokenů.  
  
|Typ tokenu|Generuje deklarace identity|Mapy do tokenu přístupu k systému Windows|  
|-|-|-|  
|SAML 1.1|1.  All claims from System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope).<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey` Deklarace identity, který obsahuje serializace XML potvrzení klíče, pokud token obsahuje doklad token.<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername` Deklarace identity z elementu vystavitele.<br />4.  AuthenticationMethod a AuthenticationInstant deklarací identity, pokud je token obsahuje příkaz k ověřování.|Kromě deklarace uvedené v "SAML 1.1", s výjimkou deklarace identity typu `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`, přidá se deklarace identity a identity budou odpovídat WindowsClaimsIdentity související s ověřování systému Windows.|  
|SAML 2.0|Stejné jako "SAML 1.1".|Stejné jako "SAML 1.1 namapované na účet systému Windows".|  
|X509|1.  Deklarace identity se X500 rozlišující název, název_e-mailu, dnsName, SimpleName, UpnName, UrlName, kryptografický otisk, RsaKey (to lze extrahovat pomocí metody RSACryptoServiceProvider.ExportParameters z vlastnosti X509Certificate2.PublicKey.Key), DsaKey ( To lze extrahovat pomocí metody DSACryptoServiceProvider.ExportParameters z vlastnosti X509Certificate2.PublicKey.Key), SerialNumber vlastnosti z X509 certifikátu.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`. AuthenticationInstant deklarace identity s hodnotou čas, kdy byl certifikát ověřen ve formátu data a času XmlSchema.|1.  Používá název plně kvalifikované domény účtu systému Windows, jako `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name` hodnoty deklarace identity. .<br />2.  Deklarace identity z X509 certifikát není namapován na systému Windows a z účtu systému windows získat pomocí mapování certifikátu do systému Windows.|  
|HLAVNÍ NÁZEV UŽIVATELE|1.  Deklarace identity jsou podobná deklarace identity v části ověřování systému Windows.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`. AuthenticationInstant deklarace identity s hodnotou čas, kdy byla ověřena heslo ve formátu data a času XmlSchema.||  
|Windows (Kerberos nebo NTLM)|1.  Vytvořené z přístupového tokenu, jako například deklarace: PrimarySID, DenyOnlyPrimarySID, PrimaryGroupSID, DenyOnlyPrimaryGroupSID, GroupSID, DenyOnlySID a název<br />2.  AuthenticationMethod s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`. AuthenticationInstant s hodnotou čas, kdy Windows přístupový token vytvořený ve formátu data a času XMLSchema.||  
|Pár klíčů RSA|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` Deklarace identity s hodnotou RSAKeyValue.<br />2.  AuthenticationMethod deklarace identity s hodnotou `http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`. AuthenticationInstant deklarace identity s hodnotou čas, kdy byla ověřena klíče RSA (to znamená, že se ověřit podpis) ve formátu data a času XMLSchema.||  
  
|Typ ověřování|Identifikátor URI vygenerované v deklaraci "AuthenticationMethod"|  
|-|-|  
|Heslo|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Pomocí protokolu Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Tento parametr|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|
