---
title: Vytváření Můj první deklaracemi webové aplikace ASP.NET
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7e36ec5b824f60057ce7b1f18c695607cf9b88a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399662"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a>Vytváření Můj první deklaracemi webové aplikace ASP.NET
## <a name="applies-to"></a>Platí pro  
  
-   Windows Identity Foundation (WIF)  
  
-   ASP.NET  
  
 Toto téma popisuje, jak pomocí technologie WIF vytvářet webové aplikace ASP.NET pracující s deklaracemi. Scénář aplikací pracujících s deklaracemi má obvykle tři účastníky, kterými jsou samotná aplikace, koncový uživatel a služba tokenů zabezpečení (STS). Tento scénář zachycuje následující obrázek:  
  
 ![WIF základní webové aplikace](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")  
  
1.  Aplikace pracující s deklaracemi zjišťují pomocí technologie WIF neověřené žádosti a směrují je na službu STS.  
  
2.  Koncový uživatel poskytne službě STS své přihlašovací údaje a po úspěšném ověření uživatele vystaví služba STS token.  
  
3.  Uživatel je přesměrován ze služby STS na aplikaci pracující s deklaracemi a token vystavený službou STS je přitom obsažen v žádosti.  
  
4.  Aplikace pracující s deklaracemi je nakonfigurována tak, aby službu STS a jí vystavené tokeny považovala za důvěryhodné. Aplikace pracující s deklaracemi token ověří a analyzuje pomocí technologie WIF. Vývojáři použít vhodné WIF API a typy, například **ClaimsPrincpal** pro potřeby aplikace, jako je například implementace autorizace pro ni.  
  
 Od rozhraní .NET 4.5, WIF je součástí balíčku rozhraní .NET Framework. Přímo k dispozici v rámci třídy WIF mnohem hlubší integrace založené na deklaracích identity umožní v rozhraní .NET, což usnadňuje používat deklarace identity. Technologie WIF 4.5 umožňuje začít vyvíjet webové aplikace pracující s deklaracemi bez nutnosti instalovat další samostatné součásti. Třídy WIF jsou nyní rozloženy mezi několik sestavení. Mezi hlavní sestavení patří System.Security.Claims, System.IdentityModel a System.IdentityModel.Services.  
  
 STS je služba, která vystavuje tokeny po úspěšném ověření. Společnost Microsoft nabízí dvě služby STS, které vyhovují standardům odvětví:  
  
-   [Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) ()http://go.microsoft.com/fwlink/?LinkID=247516)  
  
-   [Služba řízení přístupu Azure systému Windows (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).  
  
 Služba AD FS 2.0 je součástí systému Windows Server R2 a může sloužit jako služba STS pro místní scénáře. Služba ACS je cloudová služba, nabízená v rámci platformy Microsoft Azure. Při sestavování aplikací pracujících s deklaracemi můžete pro testovací nebo vzdělávací účely použít také jinou službu STS. Například můžete použít místní službu tokenů zabezpečení vývoj, která je součástí [identita a přístup pro sadu Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) tedy volně dostupných online.  
  
 Pokud chcete pomocí technologie WIF vytvořit svou první aplikaci ASP.NET pracující s deklaracemi, postupujte podle pokynů v jednom z následujících témat:  
  
-   [Postupy: Sestavení webové aplikace ASP.NET MVC pracující s deklaracemi pomocí WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [Postupy: Sestavení aplikace Webových formulářů ASP.NET pracující s deklaracemi pomocí WIF](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [Postupy: Sestavení aplikace ASP.NET pracující s deklaracemi s ověřováním pomocí formulářů](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s WIF](../../../docs/framework/security/getting-started-with-wif.md)
