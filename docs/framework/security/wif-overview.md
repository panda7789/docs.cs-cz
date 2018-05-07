---
title: Přehled technologie Windows Identity Foundation 4.5
ms.date: 03/30/2017
ms.assetid: 5f723345-7270-49e2-b638-b3a34bd40517
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e5d668ff2b6c79105ddb4ec3672144a188e0b78c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-identity-foundation-45-overview"></a>Přehled technologie Windows Identity Foundation 4.5
Windows Identity Foundation 4.5 je sada tříd rozhraní .NET Framework pro implementaci deklarovaných identit v aplikacích. Usnadňuje využívání výhod aplikací a služeb pracujících s deklaracemi. Technologii WIF 4.5 lze používat v jakékoli webové aplikaci nebo webové službě, která používá rozhraní .NET Framework 4.5 nebo novější. Technologie WIF tvoří pouze jednu část softwarové produktové řady Federated Identity společnosti Microsoft, která implementuje sdílenou vizi odvětví založenou na otevřených standardech. Federovaných identit skládá ze tří součástí: [Active Directory® Federation Services](http://go.microsoft.com/fwlink/?LinkID=247516) (AD FS) 2.0, [služby Řízení přístupu Windows Azure](http://go.microsoft.com/fwlink/?LinkID=247517) (ACS) a WIF. Společně tyto tři komponenty tvoří jádro nové platformy společnosti Microsoft pro deklarované cloudové identity a řízení přístupu.  
  
 Další informace o WIF najdete v tématu [webu Windows Identity Foundation](http://go.microsoft.com/fwlink/?LinkId=149009) (http://go.microsoft.com/fwlink/?LinkId=149009) ve středisku pro vývojáře zabezpečení na webu MSDN. Úvod do vytváření aplikace, které technologii WIF používají, najdete v části [programování technologie Windows Identity Foundation](http://go.microsoft.com/fwlink/?LinkId=210158) (http://go.microsoft.com/fwlink/?LinkId=210158) podle Vittorio Bertocci (publikováno společnosti Microsoft Press).  
  
## <a name="wif-45-features"></a>Funkce technologie WIF 4.5  
 WIF 4.5 je rozhraní pro vytváření aplikací pracujících s identitami. Toto rozhraní zajišťuje abstrakci protokolů WS-Trust a WS-Federation a nabízí vývojářům rozhraní API pro vytváření aplikací pracujících s deklaracemi, a v případě potřeby také služby tokenů zabezpečení (STS). Aplikace mohou pomocí technologie WIF zpracovávat tokeny vystavené službou STS, jako je například služba AD FS 2.0 nebo ACS, a rozhodovat se na základě identit ve webové aplikaci nebo webové službě.  
  
 Technologie WIF 4.5 nabízí následující hlavní funkce:  
  
-   Vytváření aplikací pracujících s deklaracemi (aplikací předávající strany). Technologie WIF pomáhá vývojářům vytvářet aplikace pracující s deklaracemi. Kromě toho, že poskytuje model deklarací, nabízí také bohatou sadu rozhraní API, která pomáhají na základě deklarací rozhodovat o tom, zda uživateli povolit přístup.  Technologie WIF také poskytuje vývojářům konzistentní programovací prostředí bez ohledu na to, zda se rozhodnou aplikace vytvářet s použitím technologií ASP.NET nebo WCF.  
  
-   Zajištění podpory delegování identit v aplikacích pracujících s deklaracemi.  Technologie WIF nabízí možnost zachování identity původního žadatele i přes hranice různých služeb. Této schopnosti lze dosáhnout pomocí funkce rozhraní ActAs nebo OnBehalfOf a umožňuje vývojářům přidat podporu delegování identit do aplikací pracujících s deklaracemi.  
  
-   Vytváření vlastních služeb tokenů zabezpečení (STS).  Technologie WIF podstatně usnadňuje vytváření vlastních služeb STS, které podporují protokol WS-Trust. Takové služby STS jsou označovány také jako aktivní služby STS.  
  
     Rozhraní kromě toho také poskytuje podporu pro vytváření služeb tokenů zabezpečení, které podporují protokol WS-Federation a umožňují tak používání klientů ve webových prohlížečích. Takové služby STS jsou označovány také jako pasivní služby STS.  
  
-   Nový nástroj Identity and Access Tool for Visual Studio 11, který umožňuje zabezpečit aplikaci pomocí deklarovaných identit a akceptovat uživatele od různých poskytovatelů identit. Tento nástroj WIF si můžete stáhnout z následující adresy URL: [ http://go.microsoft.com/fwlink/?LinkID=245849 ](http://go.microsoft.com/fwlink/?LinkID=245849) nebo přímo z v rámci sadu Visual Studio 11 vyhledáním "identity" přímo ve Správci rozšíření. Další informace najdete v tématu [identita a přístup pro sadu Visual Studio 2012](../../../docs/framework/security/identity-and-access-tool-for-vs.md).  
  
 Technologie WIF podporuje následující hlavní scénáře:  
  
-   Federace.  Technologie WIF umožňuje povolit federaci mezi dvěma nebo více partnery. Tento scénář mohou vývojáři realizovat díky podpoře vytváření aplikací pracujících s deklaracemi (předávajících stran) a vlastních služeb tokenů zabezpečení (STS).  
  
-   Delegování identity.  Technologie WIF usnadňuje zachování identity přes hranice služeb, což vývojářům umožňuje realizovat scénář delegování identity.  
  
-   Stupňované ověřování. Požadavky na ověřování se v aplikaci mohou pro různé prostředky lišit. Technologie WIF umožňuje vývojářům vytvářet aplikace, které mohou mít stupňované požadavky na ověřování (například ověření pomocí uživatelského jména a hesla při prvotním přihlášení a následné povýšení na ověření pomocí čipové karty).  
  
 Technologie WIF vám usnadní využívání výhod modelu deklarovaných identit. Další informace najdete v tématu [Windows Identity Foundation White Paper pro vývojáře](http://download.microsoft.com/download/7/d/0/7d0b5166-6a8a-418a-addd-95ee9b046994/windowsidentityfoundationwhitepaperfordevelopers-rtw.pdf).
