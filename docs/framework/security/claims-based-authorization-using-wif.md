---
title: Deklarace identity na základě autorizaci s použitím WIF
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 1d2972ccef6829a2b7a052ba30258086443bd833
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="claims-based-authorization-using-wif"></a>Deklarace identity na základě autorizaci s použitím WIF
V aplikaci předávající strany autorizace určuje, k jakým prostředkům má ověřená identita povolen přístup a jaké operace s těmito prostředky smí provádět. Nesprávná nebo slabá autorizace může vést k úniku informací nebo neoprávněným úpravám dat. Toto téma popisuje, jak webové aplikace a služby technologie ASP.NET pracující s deklaracemi mohou implementovat autorizaci s použitím technologie Windows Identity Foundation (WIF) a služby tokenů zabezpečení (STS), jako je například Služba řízení přístupu Microsoft Azure (ACS).  
  
## <a name="overview"></a>Přehled  
 Již od své první verze nabízí rozhraní .NET Framework flexibilní mechanismus pro implementaci autorizace. Tento mechanismus je založen na dva jednoduché rozhraní –**IPrincipal** a **identita**. Konkrétní implementace třídy **identita** představují ověřeného uživatele. Například **WindowsIdentity** implementace představuje uživatele, který je ověřována služby Active Directory a **GenericIdentity** představuje uživatele, jehož identita je ověřený pomocí vlastní Proces ověřování. Konkrétní implementace třídy **IPrincipal** nápovědy ke kontrole oprávnění pomocí role v závislosti na úložiště rolí. Například **WindowsPrincipal** kontroluje **WindowsIdentity** pro členství ve skupinách služby Active Directory. Tato kontrola se provádí pomocí volání **IsInRole** metodu **IPrincipal** rozhraní. Kontrola přístupu na základě rolí se nazývá řízení přístupu na základě rolí (RBAC). Další informace najdete v tématu [řízení přístupu na základě Role](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).  Deklarace mohou přenášet informace o rolích a podporovat tak známé mechanismy ověřování na základě rolí.  
  
 Deklarace také umožňují složitější rozhodování o autorizaci než pouze s použitím rolí. Deklarace identity může být založen na prakticky všechny informace o uživateli - stáří, PSČ, velikosti, atd. Mechanismus řízení přístupu, založený na libovolný deklarace identity se nazývá autorizace založené na deklaracích identity. Další informace najdete v tématu [založené na deklaracích identity autorizace](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Řízení přístupu na základě rolí  
 RBAC představuje přístup k autorizaci, v rámci něhož aplikace spravuje a vynucuje uživatelská oprávnění na základě rolí uživatelů. Má-li uživatel roli, která je vyžadována k provedení určité akce, je mu udělen přístup. V opačném případě je přístup odepřen.  
  
### <a name="iprincipalisinrole-method"></a>Metoda IPrincipal.IsInRole  
 Chcete-li implementovat přístup RBAC v deklaracemi identity aplikace, použijte **IsInRole()** metoda v **IPrinicpal** rozhraní, stejně jako v jiných deklaracemi identity aplikace. Existuje několik způsobů použití **IsInRole()** metoda:  
  
-   Explicitní volání na **IPrincipal.IsInRole("Administrator")**. Při použití tohoto přístupu je výsledkem logická hodnota, kterou můžete používat v podmíněných příkazech. Toto volání lze používat kdekoli v kódu.  
  
-   Pomocí zabezpečení vyžádání **PrincipalPermission.Demand()**. Při použití tohoto přístupu je výsledkem výjimka, pokud není požadavek splněn. Tento přístup můžete zapracovat do své strategie pro zpracování výjimek. Vyvolání výjimek je výrazně dražší, z hlediska výkonu ve srovnání s vrací logickou hodnotu. Tento přístup lze používat kdekoli v kódu.  
  
-   Pomocí deklarativní atributů **[PrincipalPermission (SecurityAction.Demand, Role = "Správce")]**. Tento přístup se nazývá deklarativní, protože slouží pro úpravu metody. Nelze jej používat v blocích kódu uvnitř implementace metody. Výsledkem je výjimka, pokud není požadavek splněn. Musíte ji zohlednit ve své strategii zpracování výjimek.  
  
-   Pomocí autorizace adres URL, pomocí  **\<autorizace >** kapitoly **web.config**. Tento přístup je vhodný, pokud autorizaci řídíte na úrovni adres URL. Ze všech dříve zmíněných přístupů se jedná o způsob použití na nejméně podrobné úrovni. Výhodou tohoto přístupu je, že se změny provádějí v konfiguračním souboru, což znamená, že je možné změny využívat bez nutnosti kompilace kódu.  
  
### <a name="expressing-roles-as-claims"></a>Vyjádření rolí jako deklarací  
 Když **IsInRole()** metoda je volána, není zkontroluje se, zda má aktuální uživatel tuto roli. V aplikacích pracujících s deklaracemi je role vyjádřena pomocí deklarace typu Role, která by měla být k dispozici v tokenu. Deklarace typu Role je vyjádřena pomocí následujícího identifikátoru URI:  
  
 http://schemas.microsoft.com/ws/2008/06/identity/claims/role  
  
 K dispozici je několik možností, jak do tokenu doplnit deklaraci typu Role:  
  
-   **Při vystavování tokenů**. Po ověření uživatele roli deklaraci identity vystavit poskytovatele identit služby tokenů zabezpečení nebo poskytovatel federace například Windows Azure přístup k řízení služby (ACS).  
  
-   **Transformace libovolný deklarace identity do typu deklarace role pomocí ClaimsAuthenticationManager**. ClaimsAuthenticationManager je komponenta, která je dodávána jako součást technologie WIF. Umožňuje zachytávat žádosti při spuštění aplikace, kontrolovat tokeny a transformovat je pomocí přidání, změny nebo odebrání deklarací. Další informace o tom, jak používat ClaimsAuthenticationManager pro transformaci deklarací identity najdete v tématu [postupy: implementace Role na základě řízení přístupu (RBAC) v deklaracích vědět ASP.NET aplikace pomocí WIF a ACS](http://go.microsoft.com/fwlink/?LinkID=247445) (http://go.microsoft.com/fwlink/?LinkID=247444).  
  
-   **Mapování libovolné deklarace typu role použít konfigurační sekci samlSecurityTokenRequirement**– deklarativní přístup, kde se provádí transformaci deklarací identity pomocí pouze konfiguraci a žádné kódování se vyžaduje.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autorizace na základě rolí  
 Autorizace na základě deklarací je přístup, v rámci něhož autorizační rozhodnutí udělit nebo odepřít přístup vychází z libovolné logiky využívající data, která jsou k dispozici v deklaracích. Připomínáme, že v případě řízení přístupu RBAC se využívala jediná deklarace, a to deklarace typu Role. Deklarace typu Role umožňovala zjistit, zda uživatel patří či nepatří do určité role. Proces rozhodování o autorizaci s použitím autorizace na základě deklarací ilustrují následující kroky:  
  
1.  Aplikace obdrží žádost, která vyžaduje ověření uživatele.  
  
2.  Technologie WIF přesměruje uživatele na jeho poskytovatele identity. Po ověření uživatele je aplikaci předložena žádost, k níž je přidružen token zabezpečení reprezentující uživatele a obsahující deklarace o uživateli. Technologie WIF přidruží tyto deklarace k objektu zabezpečení, který uživatele reprezentuje.  
  
3.  Aplikace předá deklarace mechanismu, který implementuje rozhodovací logiku. Může to být kód v paměti, volání webové služby, dotaz do databáze, propracovaný modul pravidel nebo komponenta ClaimsAuthorizationManager.  
  
4.  Rozhodovací mechanismus vypočítá výsledek na základě deklarací.  
  
5.  Přístup je udělen, pokud je výsledkem hodnota true, a odepřen, pokud je výsledkem hodnota false. Pravidlo například může být, že věk uživatele je minimálně 21 let a žije ve státě Washington.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> je užitečné pro externího rozhodnutí logiku pro ověření na základě deklarace identity ve svých aplikacích. ClaimsAuthenticationManager je komponenta technologie WIF, která je dodávána jako součást technologie .NET 4.5. Komponenta ClaimsAuthorizationManager umožňuje zachytávat příchozí žádosti a implementovat jakoukoli logiku, která rozhoduje o autorizaci na základě obdržených deklarací. To je důležité, pokud je potřeba logiku autorizace změnit. V takovém případě používání komponenty ClaimsAuthorizationManager neovlivní integritu aplikace, a tím snižuje pravděpodobnost chyby v aplikaci v důsledku této změny. Další informace o tom, jak používat ClaimsAuthorizationManager implementovat řízení přístupu založené na deklaracích identity najdete v tématu [postupy: implementace autorizaci deklarací identity v deklaracích vědět ASP.NET aplikace pomocí WIF a ACS](http://go.microsoft.com/fwlink/?LinkID=247446).
