---
title: Sestavení první služby WCF pracující s deklaracemi
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 13a17473388582e5fa72cd8d335b6a05204ea509
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306609"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Sestavení první služby WCF pracující s deklaracemi
## <a name="applies-to"></a>Platí pro  
  
-   Windows Identity Foundation (WIF)  
  
-   Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje, jak pomocí technologie WIF vytvářet webové služby WCF pracující s deklaracemi. Scénář webových služeb pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná webová služba, koncový uživatel a služba tokenů zabezpečení (STS). Tento scénář zachycuje následující obrázek:  
  
 ![Diagram zobrazující komponenty technologie WIF základní deklarace identity používající službu WCF.](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. Klient služby WCF (někdy označovaný jako agent) odesílá pověření službě STS pomocí technologie WIF a po úspěšném ověření vystaví služba STS agentovi token.  
  
2. Tento token vystavený službou STS odešle agent službě WCF.  
  
3. Služba WCF pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné. Služba WCF pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF. Vývojáři používají příslušná rozhraní API technologie WIF a typy, například **ClaimsPrincipal** pro potřeby aplikace, jako je například implementace autorizace.  
  
 Počínaje .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework. V rozhraní .NET, což usnadňuje používání deklarací tříd WIF přímo k dispozici v rozhraní umožňuje mnohem hlubší integraci deklarovaných identit. Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti. Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.  
  
 STS je služba, která vystavuje tokeny po úspěšném ověření. Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:  
  
-   [Active Directory Federation Services (AD FS) 2.0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
-   [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře. Azure Active Directory Access Control (označované také jako Access Control Service nebo ACS) je Cloudová služba, nabízená v rámci Microsoft Azure. Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS. Například můžete použít místní službu STS, která je součástí [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) což je volně k dispozici online.  
  
 Sestavit první s deklaracemi identity služby WCF pomocí technologie WIF, najdete v tématu [How To: Povolení WIF pro aplikaci webové služby WCF](../../../docs/framework/security/how-to-enable-wif-for-a-wcf-web-service-application.md).
  
## <a name="see-also"></a>Viz také:

- [Začínáme s WIF](../../../docs/framework/security/getting-started-with-wif.md)
