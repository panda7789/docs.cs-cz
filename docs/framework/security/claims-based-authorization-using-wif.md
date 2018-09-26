---
title: Pomocí technologie WIF autorizace deklarovaných identit
ms.date: 03/30/2017
ms.assetid: e24000a3-8fd8-4c0e-bdf0-39882cc0f6d8
author: BrucePerlerMS
ms.openlocfilehash: c13ea5c9f2f62c9c01139741d06de35dd2ff4be1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088110"
---
# <a name="claims-based-authorization-using-wif"></a>Pomocí technologie WIF autorizace deklarovaných identit
V aplikaci předávající strany autorizace určuje, k jakým prostředkům má ověřená identita povolen přístup a jaké operace s těmito prostředky smí provádět. Nesprávná nebo slabá autorizace může vést k úniku informací nebo neoprávněným úpravám dat. Toto téma popisuje, jak webové aplikace a služby technologie ASP.NET pracující s deklaracemi mohou implementovat autorizaci s použitím technologie Windows Identity Foundation (WIF) a služby tokenů zabezpečení (STS), jako je například Služba řízení přístupu Microsoft Azure (ACS).  
  
## <a name="overview"></a>Přehled  
 Již od své první verze nabízí rozhraní .NET Framework flexibilní mechanismus pro implementaci autorizace. Tento mechanismus je založen na dvou jednoduchých rozhraních –**IPrincipal** a **IIdentity**. Konkrétní implementace **IIdentity** reprezentují ověřené uživatele. Například **WindowsIdentity** implementace představuje uživatele, který je ověřen službou Active Directory, a **GenericIdentity** představuje uživatele, jehož identita je ověřena prostřednictvím vlastního Proces ověřování. Konkrétní implementace **IPrincipal** pomáhají kontrolovat oprávnění s použitím rolí v závislosti na úložišti rolí. Například **WindowsPrincipal** kontroluje **WindowsIdentity** pro členství ve skupinách služby Active Directory. Tato kontrola se provádí pomocí volání **IsInRole** metodu **IPrincipal** rozhraní. Kontrola přístupu na základě rolí se nazývá řízení přístupu na základě rolí (RBAC). Další informace najdete v tématu [řízení přístupu na základě Role](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_1).  Deklarace mohou přenášet informace o rolích a podporovat tak známé mechanismy ověřování na základě rolí.  
  
 Deklarace také umožňují složitější rozhodování o autorizaci než pouze s použitím rolí. Deklarace může být založen na prakticky jakékoli informaci o uživateli - věk, poštovní směrovací číslo, velikost bot atd. Mechanismus řízení přístupu, který je založený na libovolných deklaracích se nazývá autorizace na základě rolí. Další informace najdete v tématu [autorizace na základě rolí](../../../docs/framework/security/claims-based-authorization-using-wif.md#BKMK_2).  
  
<a name="BKMK_1"></a>   
## <a name="role-based-access-control"></a>Řízení přístupu na základě rolí  
 RBAC představuje přístup k autorizaci, v rámci něhož aplikace spravuje a vynucuje uživatelská oprávnění na základě rolí uživatelů. Má-li uživatel roli, která je vyžadována k provedení určité akce, je mu udělen přístup. V opačném případě je přístup odepřen.  
  
### <a name="iprincipalisinrole-method"></a>Metoda IPrincipal.IsInRole  
 Chcete-li v deklaracemi implementovat přístup RBAC, použijte **IsInRole()** metoda ve **IPrinicpal** rozhraní, stejně jako v jiných deklaracemi identity aplikace. Existuje několik způsobů použití **IsInRole()** metody:  
  
-   Explicitně pomocí volání **IPrincipal.IsInRole("Administrator")**. Při použití tohoto přístupu je výsledkem logická hodnota, kterou můžete používat v podmíněných příkazech. Toto volání lze používat kdekoli v kódu.  
  
-   Pomocí požadavku zabezpečení **PrincipalPermission.Demand()**. Při použití tohoto přístupu je výsledkem výjimka, pokud není požadavek splněn. Tento přístup můžete zapracovat do své strategie pro zpracování výjimek. Je vyvolání výjimky mnohem nákladnější z hlediska výkonu ve srovnání s vrací datový typ Boolean. Tento přístup lze používat kdekoli v kódu.  
  
-   Pomocí deklarativních atributů **[PrincipalPermission (SecurityAction.Demand, Role = "Správce")]**. Tento přístup se nazývá deklarativní, protože slouží pro úpravu metody. Nelze jej používat v blocích kódu uvnitř implementace metody. Výsledkem je výjimka, pokud není požadavek splněn. Musíte ji zohlednit ve své strategii zpracování výjimek.  
  
-   Použitím autorizace adres URL, pomocí  **\<autorizace >** tématu **web.config**. Tento přístup je vhodný, pokud autorizaci řídíte na úrovni adres URL. Ze všech dříve zmíněných přístupů se jedná o způsob použití na nejméně podrobné úrovni. Výhodou tohoto přístupu je, že se změny provádějí v konfiguračním souboru, což znamená, že je možné změny využívat bez nutnosti kompilace kódu.  
  
### <a name="expressing-roles-as-claims"></a>Vyjádření rolí jako deklarací  
 Když **IsInRole()** metoda je volána, je kontrola se kontroluje, zda má aktuální uživatel tuto roli. V aplikacích pracujících s deklaracemi je role vyjádřena pomocí deklarace typu Role, která by měla být k dispozici v tokenu. Deklarace typu Role je vyjádřena pomocí následujícího identifikátoru URI:  
  
 http://schemas.microsoft.com/ws/2008/06/identity/claims/role  
  
 K dispozici je několik možností, jak do tokenu doplnit deklaraci typu Role:  
  
-   **Při vystavení tokenu**. Při ověření uživatele může být deklarace role vydané poskytovatelem identity STS nebo federačního zprostředkovatele, jako je například Windows Azure Access Control Service (ACS).  
  
-   **Přeměna libovolných deklarací na deklarace typu role pomocí komponenty ClaimsAuthenticationManager**. ClaimsAuthenticationManager je komponenta, která je dodávána jako součást technologie WIF. Umožňuje zachytávat žádosti při spuštění aplikace, kontrolovat tokeny a transformovat je pomocí přidání, změny nebo odebrání deklarací. Další informace o tom, jak transformovat deklarace pomocí komponenty ClaimsAuthenticationManager, naleznete v tématu [postupy: implementace Role na základě řízení přístupu (RBAC) v deklaracích vědět aplikaci ASP.NET pomocí technologie WIF a služby ACS](https://go.microsoft.com/fwlink/?LinkID=247445).  
  
-   **Mapování libovolných deklarací na typ role pomocí konfiguračního oddílu samlSecurityTokenRequirement**– deklarativní přístup, kde se provádí transformaci deklarací pomocí jenom konfigurace a bez kódování je povinný.  
  
<a name="BKMK_2"></a>   
## <a name="claims-based-authorization"></a>Autorizace na základě rolí  
 Autorizace na základě deklarací je přístup, v rámci něhož autorizační rozhodnutí udělit nebo odepřít přístup vychází z libovolné logiky využívající data, která jsou k dispozici v deklaracích. Připomínáme, že v případě řízení přístupu RBAC se využívala jediná deklarace, a to deklarace typu Role. Deklarace typu Role umožňovala zjistit, zda uživatel patří či nepatří do určité role. Proces rozhodování o autorizaci s použitím autorizace na základě deklarací ilustrují následující kroky:  
  
1.  Aplikace obdrží žádost, která vyžaduje ověření uživatele.  
  
2.  Technologie WIF přesměruje uživatele na jeho poskytovatele identity. Po ověření uživatele je aplikaci předložena žádost, k níž je přidružen token zabezpečení reprezentující uživatele a obsahující deklarace o uživateli. Technologie WIF přidruží tyto deklarace k objektu zabezpečení, který uživatele reprezentuje.  
  
3.  Aplikace předá deklarace mechanismu, který implementuje rozhodovací logiku. Může to být kód v paměti, volání webové služby, dotaz do databáze, propracovaný modul pravidel nebo komponenta ClaimsAuthorizationManager.  
  
4.  Rozhodovací mechanismus vypočítá výsledek na základě deklarací.  
  
5.  Přístup je udělen, pokud je výsledkem hodnota true, a odepřen, pokud je výsledkem hodnota false. Pravidlo například může být, že věk uživatele je minimálně 21 let a žije ve státě Washington.  
  
 <xref:System.Security.Claims.ClaimsAuthorizationManager> je užitečné pro rozhodovací logiku pro ověřování na základě deklarací identity ve svých aplikacích. ClaimsAuthenticationManager je komponenta technologie WIF, která je dodávána jako součást technologie .NET 4.5. Komponenta ClaimsAuthorizationManager umožňuje zachytávat příchozí žádosti a implementovat jakoukoli logiku, která rozhoduje o autorizaci na základě obdržených deklarací. To je důležité, pokud je potřeba logiku autorizace změnit. V takovém případě používání komponenty ClaimsAuthorizationManager neovlivní integritu aplikace, a tím snižuje pravděpodobnost chyby v aplikaci v důsledku této změny. Další informace o tom, jak používat ClaimsAuthorizationManager implementovat řízení přístupu podle deklarací identity najdete v tématu [postupy: implementace autorizaci deklarací identity v deklaracích vědět aplikaci ASP.NET pomocí technologie WIF a služby ACS](https://go.microsoft.com/fwlink/?LinkID=247446).
