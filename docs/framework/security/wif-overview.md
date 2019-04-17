---
title: Přehled Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
ms.openlocfilehash: 6165dbf32b777a8d82e756f84ed2415d6ed3d774
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613028"
---
# <a name="windows-identity-foundation-45-overview"></a>Přehled Windows Identity Foundation 4.5
Windows Identity Foundation 4.5 je sada tříd rozhraní .NET Framework pro implementaci deklarovaných identit v aplikacích. Usnadňuje využívání výhod aplikací a služeb pracujících s deklaracemi. Technologii WIF 4.5 lze používat v jakékoli webové aplikaci nebo webové službě, která používá rozhraní .NET Framework 4.5 nebo novější. Technologie WIF tvoří pouze jednu část softwarové produktové řady Federated Identity společnosti Microsoft, která implementuje sdílenou vizi odvětví založenou na otevřených standardech. Federované Identity se skládá ze tří součástí: [Aktivní Directory® Federation Services](https://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2.0, [Windows Azure Access Control Services](https://go.microsoft.com/fwlink/?LinkID=247517) (ACS) a technologie WIF. Společně tyto tři komponenty tvoří jádro nové platformy společnosti Microsoft pro deklarované cloudové identity a řízení přístupu.  
  
 Další informace o technologii WIF naleznete v tématu [webu Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=149009) v Centru zabezpečení pro vývojáře na webu MSDN. Úvod do vytváření aplikací pomocí technologie WIF, najdete v článku [programování technologie Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=210158) autorem je Vittorio Bertocci (vydáno nakladatelstvím Microsoft Press).  
  
## <a name="wif-45-features"></a>Funkce technologie WIF 4.5  
 WIF 4.5 je rozhraní pro vytváření aplikací pracujících s identitami. Toto rozhraní zajišťuje abstrakci protokolů WS-Trust a WS-Federation a nabízí vývojářům rozhraní API pro vytváření aplikací pracujících s deklaracemi, a v případě potřeby také služby tokenů zabezpečení (STS). Aplikace mohou pomocí technologie WIF zpracovávat tokeny vystavené službou STS, jako je například služba AD FS 2.0 nebo ACS, a rozhodovat se na základě identit ve webové aplikaci nebo webové službě.  
  
 Technologie WIF 4.5 nabízí následující hlavní funkce:  
  
-   Vytváření aplikací pracujících s deklaracemi (aplikací předávající strany). Technologie WIF pomáhá vývojářům vytvářet aplikace pracující s deklaracemi. Kromě toho, že poskytuje model deklarací, nabízí také bohatou sadu rozhraní API, která pomáhají na základě deklarací rozhodovat o tom, zda uživateli povolit přístup.  Technologie WIF také poskytuje vývojářům konzistentní programovací prostředí bez ohledu na to, zda se rozhodnou aplikace vytvářet s použitím technologií ASP.NET nebo WCF.  
  
-   Zajištění podpory delegování identit v aplikacích pracujících s deklaracemi.  Technologie WIF nabízí možnost zachování identity původního žadatele i přes hranice různých služeb. Této schopnosti lze dosáhnout pomocí funkce rozhraní ActAs nebo OnBehalfOf a umožňuje vývojářům přidat podporu delegování identit do aplikací pracujících s deklaracemi.  
  
-   Vytváření vlastních služeb tokenů zabezpečení (STS).  Technologie WIF podstatně usnadňuje vytváření vlastních služeb STS, které podporují protokol WS-Trust. Takové služby STS jsou označovány také jako aktivní služby STS.  
  
     Rozhraní kromě toho také poskytuje podporu pro vytváření služeb tokenů zabezpečení, které podporují protokol WS-Federation a umožňují tak používání klientů ve webových prohlížečích. Takové služby STS jsou označovány také jako pasivní služby STS.  
  
-   Nový nástroj Identity and Access Tool for Visual Studio 11, který umožňuje zabezpečit aplikaci pomocí deklarovaných identit a akceptovat uživatele od různých poskytovatelů identit. Tento nástroj technologie WIF si můžete stáhnout z následující adresy URL: <https://go.microsoft.com/fwlink/?LinkID=245849> nebo přímo v rámci sady Visual Studio 11 tak, že "identity" ve Správci rozšíření. Další informace najdete v tématu [Identity and Access Tool for Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
 Technologie WIF podporuje následující hlavní scénáře:  
  
-   Federace.  Technologie WIF umožňuje povolit federaci mezi dvěma nebo více partnery. Tento scénář mohou vývojáři realizovat díky podpoře vytváření aplikací pracujících s deklaracemi (předávajících stran) a vlastních služeb tokenů zabezpečení (STS).  
  
-   Delegování identity.  Technologie WIF usnadňuje zachování identity přes hranice služeb, což vývojářům umožňuje realizovat scénář delegování identity.  
  
-   Stupňované ověřování. Požadavky na ověřování se v aplikaci mohou pro různé prostředky lišit. Technologie WIF umožňuje vývojářům vytvářet aplikace, které mohou mít stupňované požadavky na ověřování (například ověření pomocí uživatelského jména a hesla při prvotním přihlášení a následné povýšení na ověření pomocí čipové karty).  
  
 Technologie WIF vám usnadní využívání výhod modelu deklarovaných identit. Další informace najdete v tématu [Windows Identity Foundation White Paper pro vývojáře](https://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf).
