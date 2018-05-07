---
title: Vytváření Můj první službu WCF používající deklarace identity
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3b88835cc7836d9d6c323de3c0386b3f4c7c3078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Vytváření Můj první službu WCF používající deklarace identity
## <a name="applies-to"></a>Platí pro  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje, jak pomocí technologie WIF vytvářet webové služby WCF pracující s deklaracemi. Scénář webových služeb pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná webová služba, koncový uživatel a služba tokenů zabezpečení (STS). Tento scénář zachycuje následující obrázek:  
  
 ![WIF Basic deklarace identity služby využívající WCF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")  
  
1.  Klient služby WCF (někdy označovaný jako agent) odesílá pověření službě STS pomocí technologie WIF a po úspěšném ověření vystaví služba STS agentovi token.  
  
2.  Tento token vystavený službou STS odešle agent službě WCF.  
  
3.  Služba WCF pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné. Služba WCF pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF. Vývojáři použít vhodné WIF API a typy, například **ClaimsPrincipal** pro potřeby aplikace, jako je například implementace autorizace pro ni.  
  
 Od rozhraní .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework. Přímo k dispozici v rámci třídy WIF mnohem hlubší integrace založené na deklaracích identity umožní v rozhraní .NET, což usnadňuje používat deklarace identity. Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti. Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.  
  
 STS je služba, která vystavuje tokeny po úspěšném ověření. Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:  
  
-   [Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) ()http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Služba řízení přístupu Azure systému Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře. Azure Active Directory řízení přístupu (také označované jako služby Řízení přístupu nebo služby ACS) je Cloudová služba, které nabízí v rámci Microsoft Azure. Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS. Například můžete použít místní službu tokenů zabezpečení vývoj, která je součástí [identita a přístup pro sadu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) tedy volně dostupných online.  
  
 Vytvoření vaší první deklaracemi identity služby WCF pomocí WIF, najdete v části [postupy: povolení WIF pro webovou aplikaci služby WCF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Viz také  
 [Začínáme s WIF](../../../docs/framework/security/getting-started-with-wif.md)
