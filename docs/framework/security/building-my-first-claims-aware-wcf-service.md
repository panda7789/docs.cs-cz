---
title: Sestavení první služby WCF pracující s deklaracemi
ms.date: 03/30/2017
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
author: BrucePerlerMS
ms.openlocfilehash: 330d785721cb434f74ec746310a71bfd39fefd0b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045553"
---
# <a name="building-my-first-claims-aware-wcf-service"></a>Sestavení první služby WCF pracující s deklaracemi
## <a name="applies-to"></a>Platí pro  
  
- Windows Identity Foundation (WIF)  
  
- Windows Communication Foundation (WCF)  
  
## <a name="overview"></a>Přehled  
 Toto téma popisuje, jak pomocí technologie WIF vytvářet webové služby WCF pracující s deklaracemi. Scénář webových služeb pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná webová služba, koncový uživatel a služba tokenů zabezpečení (STS). Tento scénář zachycuje následující obrázek:  
  
 ![Diagram znázorňující komponenty WCF WIF úrovně Basic s podporou deklarací identity](./media/building-my-first-claims-aware-wcf-service/windows-identify-foundation-basic-claims-aware-windows-communication-foundation-service.gif)  
  
1. Klient služby WCF (někdy označovaný jako agent) odesílá pověření službě STS pomocí technologie WIF a po úspěšném ověření vystaví služba STS agentovi token.  
  
2. Tento token vystavený službou STS odešle agent službě WCF.  
  
3. Služba WCF pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné. Služba WCF pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF. Vývojáři používají příslušné rozhraní API a typy WIF, například **ClaimsPrincipal** pro potřeby aplikace, jako je implementace autorizace pro IT.  
  
 Počínaje rozhraním .NET 4,5 je WIF součástí balíčku .NET Framework. Třídy WIF přímo dostupné v rozhraní umožňují mnohem hlubší integraci identity založené na deklaracích identity v rozhraní .NET, což usnadňuje používání deklarací identity. Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti. Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.  
  
 STS je služba, která vystavuje tokeny po úspěšném ověření. Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:  
  
- [Active Directory Federation Services (AD FS) (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://docs.microsoft.com/previous-versions/azure/azure-services/hh147631(v=azure.100))
  
 Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře. Azure Active Directory Access Control (označované také jako Access Control Service nebo ACS) je cloudová služba, která se nabízí jako součást Microsoft Azure. Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS. Můžete například použít místní službu STS pro vývoj, která je součástí [nástroje Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , který je volně dostupný online.  
  
 Postup sestavení první služby WCF pracující s deklaracemi pomocí WIF najdete v [tématu How to: Povolí WIF pro aplikaci](how-to-enable-wif-for-a-wcf-web-service-application.md)webové služby WCF.
  
## <a name="see-also"></a>Viz také:

- [Začínáme s WIF](getting-started-with-wif.md)
