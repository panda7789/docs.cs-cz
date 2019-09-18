---
title: Sestavení první webové aplikace ASP.NET pracující s deklaracemi
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 900ee49b4bf51eeb6e3b0c0cf6879cc12a0cb071
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045594"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Sestavení první webové aplikace ASP.NET pracující s deklaracemi
## <a name="applies-to"></a>Platí pro  
  
- Windows Identity Foundation (WIF)  
  
- ASP.NET  
  
 Toto téma popisuje, jak pomocí technologie WIF vytvářet webové aplikace ASP.NET pracující s deklaracemi. Scénář aplikací pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná aplikace, koncový uživatel a služba tokenů zabezpečení (STS). Tento scénář zachycuje následující obrázek:  
  
 ![Diagram znázorňující komponenty webové aplikace WIF Basic](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. Aplikace pracující s deklaracemi zjišťují pomocí technologie WIF neověřené žádosti a směrují je na službu STS.  
  
2. Koncový uživatel poskytne službě STS své přihlašovací údaje a po úspěšném ověření uživatele vystaví služba STS token.  
  
3. Uživatel je přesměrován ze služby STS na aplikaci pracující s deklaracemi a token vystavený službou STS je přitom obsažen v žádosti.  
  
4. Aplikace pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné. Aplikace pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF. Vývojáři používají příslušné rozhraní API a typy WIF, například **ClaimsPrincipal** pro potřeby aplikace, jako je implementace autorizace pro IT.  
  
 Počínaje rozhraním .NET 4,5 je WIF součástí balíčku .NET Framework. Třídy WIF přímo dostupné v rozhraní umožňují mnohem hlubší integraci identity založené na deklaracích identity v rozhraní .NET, což usnadňuje používání deklarací identity. Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti. Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.  
  
 STS je služba, která vystavuje tokeny po úspěšném ověření. Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:  
  
- [Active Directory Federation Services (AD FS) (AD FS) 2,0](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [Windows Azure Access Control Service (ACS)](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře. Služba ACS je cloudová služba, nabízená v rámci platformy Microsoft Azure. Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS. Můžete například použít místní službu STS pro vývoj, která je součástí [nástroje Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , který je volně dostupný online.  
  
 Pokud chcete pomocí technologie WIF vytvořit svou první aplikaci ASP.NET pracující s deklaracemi, postupujte podle pokynů v jednom z následujících témat:  
  
- [Postupy: Vytváření ASP.NET webových aplikací s podporou deklarací identity pomocí WIF](how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [Postupy: Sestavování aplikace webových formulářů ASP.NET pracující s deklaracemi pomocí WIF](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [Postupy: Vytváření aplikací ASP.NET pracujících s deklaracemi pomocí ověřování založeného na formulářích](claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s WIF](getting-started-with-wif.md)
