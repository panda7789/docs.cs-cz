---
title: Pokyny pro zabezpečení nespravovaného kódu
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec97861a9d748767199da3e1fb7f53361c3a48ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966126"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Pokyny pro zabezpečení nespravovaného kódu
Některé kódy knihoven musí volat do nespravovaného kódu (například rozhraní API nativního kódu, jako je Win32). Vzhledem k tomu, že to znamená mimo hranice zabezpečení pro spravovaný kód, je vyžadována nezbytná opatrnost. Pokud je váš kód neutrální z hlediska zabezpečení, musí mít váš kód i jakýkoli kód, který ho volá, oprávnění nespravovaného <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> kódu (<xref:System.Security.Permissions.SecurityPermission> se zadaným příznakem).  
  
 Je však často nevhodné, aby váš volající měl taková výkonná oprávnění. V takových případech může být důvěryhodný kód, podobně jako spravovaný obálka nebo kód knihovny popsané v tématu [zabezpečení kódu obálky](../../../docs/framework/misc/securing-wrapper-code.md). Pokud je základní funkce nespravovaného kódu zcela bezpečná, dá se přímo zveřejnit; v opačném případě se jako první vyžaduje vhodná kontrolní oprávnění (poptávka).  
  
 Když váš kód volá do nespravovaného kódu, ale nechcete, aby volající měli oprávnění pro přístup k nespravovanému kódu, musíte toto právo uplatnit. Kontrolní výraz blokuje procházení zásobníku na vašem snímku. Musíte mít pozor, abyste v tomto procesu nevytvořili bezpečnostní otvor. Obvykle to znamená, že musíte vyžadovat vhodné oprávnění volajících a potom použít nespravovaný kód k provedení pouze toho, co toto oprávnění povoluje a ještě více. V některých případech (například funkce získat denní čas) může být nespravovaný kód přímo vystaven volajícím bez jakýchkoli kontrol zabezpečení. V každém případě musí jakýkoliv kód, který výrazy vyhodnotit, být zodpovědný za zabezpečení.  
  
 Vzhledem k tomu, že jakýkoli spravovaný kód, který poskytuje cestu kódu do nativního kódu, je potenciální cíl pro škodlivý kód, určení, který nespravovaný kód lze bezpečně použít a jak musí být použit, vyžaduje extrémní péči. Obecně by nespravovaný kód neměl být nikdy přímo vystaven částečně důvěryhodným volajícím. Existují dva hlavní předpoklady při hodnocení bezpečnosti nespravovaného kódu v knihovnách, které jsou vyhodnoceny částečně důvěryhodným kódem:  
  
- **Funkce**. Poskytuje nespravované rozhraní API funkce, které neumožňují volajícím provádět potenciálně nebezpečné operace? Zabezpečení přístupu kódu používá oprávnění k vymáhání přístupu k prostředkům, proto zvažte, zda rozhraní API používá soubory, uživatelské rozhraní nebo vlákna nebo zda zpřístupňuje chráněné informace. V takovém případě před tím, než povolíte jeho zadání, musí zabalení spravovaného kódu vyžadovat potřebná oprávnění. Kromě toho, přestože není chráněn oprávněním, musí být přístup k paměti omezen na přísnou bezpečnost typů.  
  
- **Kontrola parametru**. Běžný útok předá neočekávaným parametrům zpřístupnění metod rozhraní API nespravovaného kódu v pokusu o jejich fungování ze specifikace. Přetečení vyrovnávací paměti pomocí indexu mimo rozsah nebo hodnot posunutí představují jeden běžný příklad tohoto typu útoku, stejně jako všechny parametry, které mohou zneužít chybu v podkladovém kódu. Proto i v případě, že je rozhraní API nespravovaného kódu funkčně bezpečné (po nezbytných požadavcích) pro částečně důvěryhodné volající, musí spravovaný kód také zkontrolovat platnost parametru vyčerpáním, aby se zajistilo, že žádná nezamýšlená volání nejsou možná ze škodlivého kódu pomocí spravovaného vrstva obálky kódu.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Používání atributu SuppressUnmanagedCodeSecurityAttribute  
 Existuje aspekt výkonu pro uplatnění a následné volání nespravovaného kódu. Pro každé takové volání systém zabezpečení automaticky požaduje oprávnění nespravovaného kódu, což vede k pokaždému procházení zásobníku. Pokud provedete vyhodnocení a ihned volání nespravovaného kódu, procházení zásobníku může být nevýznamné: skládá se z vašeho kontrolního výrazu a volání nespravovaného kódu.  
  
 Vlastní atribut s názvem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> lze použít na vstupní body nespravovaného kódu, aby bylo možné zakázat normální kontrolu <xref:System.Security.Permissions.SecurityPermission> zabezpečení, <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> která vyžaduje zadané oprávnění. Při tomto postupu je třeba vzít v úvahu extrémní opatrnost, protože tato akce vytvoří otevřené dveře do nespravovaného kódu bez kontrol zabezpečení za běhu. Je třeba poznamenat, že i když bylo použito **SuppressUnmanagedCodeSecurityAttribute** , existuje jednorázová kontrola zabezpečení, ke které dojde při kompilaci JIT (just-in-time) k zajištění, že okamžitý volající má oprávnění k volání nespravovaného kódu.  
  
 Pokud použijete **SuppressUnmanagedCodeSecurityAttribute**, podívejte se na následující body:  
  
- Zpřístupněte vstupní bod nespravovaného kódu jako interní nebo jinak nepřístupný mimo váš kód.  
  
- Jakékoli volání do nespravovaného kódu je potenciální bezpečnostní otvor. Ujistěte se, že váš kód není portálem pro škodlivý kód pro nepřímo se zavoláním do nespravovaného kódu a vyhnete se kontrole zabezpečení. V případě potřeby oprávnění na vyžádání.  
  
- Použijte konvenci pojmenování k explicitní identifikaci při vytváření nebezpečné cesty k nespravovanému kódu, jak je popsáno v následující části.  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Konvence pojmenování pro metody nespravovaného kódu  
 Pro pojmenovávání metod nespravovaného kódu se vytvořila užitečná a vysoce doporučená konvence. Všechny metody nespravovaného kódu jsou rozdělené do tří kategorií: **bezpečné**, **nativní**a **nebezpečné**. Tato klíčová slova lze použít jako názvy tříd, v rámci kterých jsou definovány různé druhy vstupních bodů nespravovaného kódu. Ve zdrojovém kódu by tato klíčová slova měla být přidána do názvu třídy, `Safe.GetTimeOfDay`jako `Native.Xyz`v, `Unsafe.DangerousAPI`nebo například. Každé z těchto klíčových slov poskytuje užitečné informace o zabezpečení pro vývojáře využívající tuto třídu, jak je popsáno v následující tabulce.  
  
|Klíčové slovo|Důležité informace o zabezpečení|  
|-------------|-----------------------------|  
|**odvod**|Zcela neškodný pro jakýkoliv kód, dokonce i škodlivý kód, který se má volat. Dá se použít stejně jako jiný spravovaný kód. Například funkce, která získá denní čas, je obvykle bezpečná.|  
|**nativní**|Zabezpečení neutrální; To znamená, že nespravovaný kód, který vyžaduje oprávnění nespravovaného kódu pro volání. Kontroluje se zabezpečení, které zastaví neoprávněného volajícího.|  
|**unsafe**|Potenciálně nebezpečný vstupní bod nespravovaného kódu s potlačeným zabezpečením. Vývojáři by měli při použití takového nespravovaného kódu využít největší opatrnost, aby se zajistila ochrana před ohrožením zabezpečení. Vývojáři musí být odpovědni, protože toto klíčové slovo Přepisuje systém zabezpečení.|  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
