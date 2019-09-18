---
title: Autorizace deklarovaných identit pomocí WIF
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: ebf4c28bd2a46c21535b596af22d1fa420d20e71
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045492"
---
# <a name="claims-based-authorization-using-wif"></a>Autorizace deklarovaných identit pomocí WIF
V aplikaci předávající strany autorizace určuje, k jakým prostředkům má ověřená identita povolen přístup a jaké operace s těmito prostředky smí provádět. Nesprávná nebo slabá autorizace může vést k úniku informací nebo neoprávněným úpravám dat. Toto téma popisuje, jak webové aplikace a služby technologie ASP.NET pracující s deklaracemi mohou implementovat autorizaci s použitím technologie Windows Identity Foundation (WIF) a služby tokenů zabezpečení (STS), jako je například Služba řízení přístupu Microsoft Azure (ACS).  
  
## <a name="overview"></a>Přehled  
 Již od své první verze nabízí rozhraní .NET Framework flexibilní mechanismus pro implementaci autorizace. Tento mechanismus je založen na dvou jednoduchých rozhraních –**IPrincipal** a **IIdentity**. Konkrétní implementace **IIdentity** reprezentují ověřeného uživatele. Například implementace **WindowsIdentity** představuje uživatele, který je ověřený službou Active Directory, a **GenericIdentity** představuje uživatele, jehož identita je ověřena prostřednictvím vlastního procesu ověřování. Konkrétní implementace **IPrincipal** umožňují kontrolovat oprávnění pomocí rolí v závislosti na úložišti rolí. Například **WindowsPrincipal** **kontroluje pro** členství ve skupinách služby Active Directory. Tato kontroly se provádí voláním metody **IsInRole** v rozhraní **IPrincipal** . Kontrola přístupu na základě rolí se nazývá řízení přístupu na základě rolí (RBAC). Další informace najdete v tématu [Access Control na základě rolí](claims-based-authorization-using-wif.md#BKMK_1).  Deklarace mohou přenášet informace o rolích a podporovat tak známé mechanismy ověřování na základě rolí.  
  
 Deklarace také umožňují složitější rozhodování o autorizaci než pouze s použitím rolí. Deklarace identity můžou být založené na prakticky jakýchkoli informacích o stáří uživatele, PSČ, velikosti obuvi atd. Mechanismus řízení přístupu založený na libovolných deklaracích se nazývá ověřování na základě deklarací identity. Další informace najdete v tématu [ověřování na základě deklarací identity](claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Řízení přístupu na základě rolí  
 RBAC představuje přístup k autorizaci, v rámci něhož aplikace spravuje a vynucuje uživatelská oprávnění na základě rolí uživatelů. Má-li uživatel roli, která je vyžadována k provedení určité akce, je mu udělen přístup. V opačném případě je přístup odepřen.  
  
### <a name="iprincipalisinrole-method"></a>Metoda IPrincipal.IsInRole  
 K implementaci přístupu RBAC v aplikacích pracujících s deklaracemi použijte metodu **IsInRole ()** v rozhraní **IPrincipal** , stejně jako v aplikacích nepracujících s deklaracemi. Existuje několik způsobů použití metody **IsInRole ()** :  
  
- Explicitní volání **IPrincipal. IsInRole ("Administrator")** . Při použití tohoto přístupu je výsledkem logická hodnota, kterou můžete používat v podmíněných příkazech. Toto volání lze používat kdekoli v kódu.  
  
- Pomocí požadavku na zabezpečení **PrincipalPermission. Demand ()** . Při použití tohoto přístupu je výsledkem výjimka, pokud není požadavek splněn. Tento přístup můžete zapracovat do své strategie pro zpracování výjimek. Vyvolávání výjimek je mnohem dražší z hlediska výkonu v porovnání s návratovou logickou hodnotou. Tento přístup lze používat kdekoli v kódu.  
  
- Použití deklarativních atributů **[PrincipalPermission (SecurityAction. Demand, role = "správce")]** . Tento přístup se nazývá deklarativní, protože slouží pro úpravu metody. Nelze jej používat v blocích kódu uvnitř implementace metody. Výsledkem je výjimka, pokud není požadavek splněn. Musíte ji zohlednit ve své strategii zpracování výjimek.  
  
- Použití autorizace  **\<** adresy URL – v části Authorization > v **souboru Web. config**. Tento přístup je vhodný, pokud autorizaci řídíte na úrovni adres URL. Ze všech dříve zmíněných přístupů se jedná o způsob použití na nejméně podrobné úrovni. Výhodou tohoto přístupu je, že se změny provádějí v konfiguračním souboru, což znamená, že je možné změny využívat bez nutnosti kompilace kódu.  
  
### <a name="expressing-roles-as-claims"></a>Vyjádření rolí jako deklarací  
 Při volání metody **IsInRole ()** se zobrazí, zda má aktuální uživatel tuto roli. V aplikacích pracujících s deklaracemi je role vyjádřena pomocí deklarace typu Role, která by měla být k dispozici v tokenu. Deklarace typu Role je vyjádřena pomocí následujícího identifikátoru URI:  
  
 `http://schemas.microsoft.com/ws/2008/06/identity/claims/role`
  
 K dispozici je několik možností, jak do tokenu doplnit deklaraci typu Role:  
  
- **Během vystavení tokenu**. Když je uživatel ověřený, může být deklarace identity vydaná poskytovatelem identity STS nebo zprostředkovatelem federace, jako je například služba Windows Azure Access Control Service (ACS).  
  
- **Transformace libovolných deklarací na typ role deklarací identity pomocí komponenty ClaimsAuthenticationManager**. ClaimsAuthenticationManager je komponenta, která je dodávána jako součást technologie WIF. Umožňuje zachytávat žádosti při spuštění aplikace, kontrolovat tokeny a transformovat je pomocí přidání, změny nebo odebrání deklarací. Další informace o použití komponenty ClaimsAuthenticationManager pro transformaci deklarací identity najdete v tématu [How to: Implementujte Access Control na základě rolí (RBAC) v aplikaci ASP.NET pracující s deklaracemi pomocí](https://go.microsoft.com/fwlink/?LinkID=247445)WIF a ACS.  
  
- **Mapování libovolných deklarací na typ role pomocí konfiguračního oddílu samlSecurityTokenRequirement**– deklarativní přístup, při kterém je transformace deklarací provedeno pouze pomocí konfigurace, a není vyžadováno kódování.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autorizace na základě rolí  
 Autorizace na základě deklarací je přístup, v rámci něhož autorizační rozhodnutí udělit nebo odepřít přístup vychází z libovolné logiky využívající data, která jsou k dispozici v deklaracích. Připomínáme, že v případě řízení přístupu RBAC se využívala jediná deklarace, a to deklarace typu Role. Deklarace typu Role umožňovala zjistit, zda uživatel patří či nepatří do určité role. Proces rozhodování o autorizaci s použitím autorizace na základě deklarací ilustrují následující kroky:  
  
1. Aplikace obdrží žádost, která vyžaduje ověření uživatele.  
  
2. Technologie WIF přesměruje uživatele na jeho poskytovatele identity. Po ověření uživatele je aplikaci předložena žádost, k níž je přidružen token zabezpečení reprezentující uživatele a obsahující deklarace o uživateli. Technologie WIF přidruží tyto deklarace k objektu zabezpečení, který uživatele reprezentuje.  
  
3. Aplikace předá deklarace mechanismu, který implementuje rozhodovací logiku. Může to být kód v paměti, volání webové služby, dotaz do databáze, propracovaný modul pravidel nebo komponenta ClaimsAuthorizationManager.  
  
4. Rozhodovací mechanismus vypočítá výsledek na základě deklarací.  
  
5. Přístup je udělen, pokud je výsledkem hodnota true, a odepřen, pokud je výsledkem hodnota false. Pravidlo například může být, že věk uživatele je minimálně 21 let a žije ve státě Washington.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager>je užitečné pro přenesení rozhodovací logiku pro ověřování na základě deklarací identity ve vašich aplikacích. ClaimsAuthenticationManager je komponenta technologie WIF, která je dodávána jako součást technologie .NET 4.5. Komponenta ClaimsAuthorizationManager umožňuje zachytávat příchozí žádosti a implementovat jakoukoli logiku, která rozhoduje o autorizaci na základě obdržených deklarací. To je důležité, pokud je potřeba logiku autorizace změnit. V takovém případě používání komponenty ClaimsAuthorizationManager neovlivní integritu aplikace, a tím snižuje pravděpodobnost chyby v aplikaci v důsledku této změny. Další informace o tom, jak používat ClaimsAuthorizationManager k implementaci řízení přístupu na základě deklarace identity, [najdete v tématu How to: Implementujte autorizaci deklarací identit v aplikaci ASP.NET pracující s deklaracemi](https://go.microsoft.com/fwlink/?LinkID=247446)pomocí WIF a ACS.
