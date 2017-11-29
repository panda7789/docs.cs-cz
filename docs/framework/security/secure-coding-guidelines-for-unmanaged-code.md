---
title: "Pokyny pro zabezpečení nespravovaného kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b6eec726342381f7e3ec71aeedd2ff012bc6c3e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Pokyny pro zabezpečení nespravovaného kódu
Kód knihovny musí volat nespravovaný kód (například nativního kódu rozhraní API, jako je například Win32). Protože to znamená přechod mimo zónu zabezpečení pro spravovaný kód, přičemž se řádně upozornění je vyžadován. Pokud je váš kód zabezpečení jazykově neutrální, kód a kód, který se volá musí mít nespravovaného kódu oprávnění (<xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zadaného příznaku).  
  
 Často je však nepřiměřený pro vaše volající takové výkonné oprávnění. V takových případech může být důvěryhodný kód prostředník, podobně jako spravovaná obálka nebo kód knihovny popsané v [zabezpečení kódu obálky](../../../docs/framework/misc/securing-wrapper-code.md). Pokud je základní funkce nespravovaného kódu zcela bezpečná, se mohou být přímo zpřístupněny; v opačném vhodná oprávnění kontrola (vyžádání), je nutné nejprve.  
  
 Pokud váš kód zavolá do nespravovaného kódu, ale nechcete vyžadovat vašim volajícím oprávnění k přístupu k nespravovaného kódu, musíte vyhodnotit tato práva. Kontrolní výrazy blokují procházení zásobníku ve vašem rámce. Musíte být opatrní, nevytvářejte v tomto procesu bezpečnostní riziko. Obvykle to znamená, že musíte požadovat vhodná oprávnění z vašich volajících a pak pomocí nespravovaného kódu provádět jenom umožňuje toto oprávnění a žádné další. V některých případech (například funkci get-hodiny) mohou být nespravovaného kódu přímo zpřístupněny volající bez jakýchkoli kontrol zabezpečení. Kód, který se vyhodnotí v každém případě musí převzít odpovědnost za zabezpečení.  
  
 Protože spravovaný kód, který poskytuje cestu kódu do nativního kódu je potenciální cíl pro škodlivý kód, určení, které nespravovaného kódu můžete bezpečně používat a jak se musí použít vyžaduje mimořádně pečlivě. Obecně platí nespravovaného kódu by nikdy být zveřejněné přímo částečně důvěryhodné volající. Existují dvě primární úvahy při hodnocení bezpečnosti použití nespravovaného kódu v knihovnách, které jsou volány částečně důvěryhodným kódem:  
  
-   **Funkce**. Poskytuje nespravovaného rozhraní API funkce, které neumožňuje volajícím provádět potenciálně nebezpečné operace? Zabezpečení přístupu kódu používá oprávnění k vynucení přístupu k prostředkům, takže zvažte, zda soubory, uživatelské rozhraní, používá rozhraní API nebo dělení na vlákna, nebo zda poskytuje chráněné informace. Pokud ano, musí spravovaného kódu zabalení je vyžadovat potřebná oprávnění před povolením ke vstupu. Kromě toho když není chráněn oprávnění, přístup do paměti pouze přísnou bezpečnost typů.  
  
-   **Kontrola parametrů**. Běžný útok předá neočekávané parametry do vystavených metody nespravovaného kódu rozhraní API ve snaze způsobit jejich provoz mimo specifikace. Způsobí přetečení vyrovnávací paměti pomocí indexu out-of-range nebo hodnoty posunu jsou běžné příkladem tento typ útoku, jako jsou všechny parametry, které může zneužít chyby v kódu. Proto i v případě nespravovaného kódu rozhraní API je funkčně bezpečné (po nezbytných požadavcích) pro částečně důvěryhodné volající, spravovaný kód musí také kontrolovat platnost parametru podrobně, aby zajistěte, aby žádné nežádoucí volání z škodlivý kód pomocí spravovaný kód obálky vrstvy.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Používání atributu SuppressUnmanagedCodeSecurityAttribute  
 Není aspekt výkonu k uplatňování a následné volání nespravovaného kódu. Pro každé takové volání systém zabezpečení automaticky požaduje oprávnění nespravovaného kódu, což vede k procházení zásobníku pokaždé, když. Pokud vyhodnocujete a okamžitě volat nespravovaný kód, může být procházení zásobníku smysl: skládá se z vašeho vyhodnocení a volání nespravovaného kódu.  
  
 Vlastní atribut nazvaný <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> lze použít k zakázání kontroly normální zabezpečení, která požaduje vstupní body nespravovaného kódu <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> oprávnění zadaný. Extrémně opatrní musí být provedeny vždy, když to, protože tato akce vytvoří otevřené dveře do nespravovaného kódu se zabezpečení runtime ověří. Je potřeba poznamenat, i když **SuppressUnmanagedCodeSecurityAttribute** použít, je kontrolu jednorázové zabezpečení, která se odehrává na kompilace v běhu (JIT) zkontrolujte, zda bezprostředního volajícího má oprávnění k volání nespravovaný kód.  
  
 Pokud použijete **SuppressUnmanagedCodeSecurityAttribute**, zkontrolujte následující body:  
  
-   Vstupní bod nespravovaného kódu nastavit vnitřní nebo jinak nedostupná mimo váš kód.  
  
-   Každé volání nespravovaného kódu je potenciální bezpečnostní riziko. Ujistěte se, že kód není portál pro škodlivý kód nepřímo volat nespravovaný kód a zamezit tak kontrolu zabezpečení. Požadujte oprávnění podle potřeby.  
  
-   Použijte zásady vytváření názvů pro explicitní identifikaci při vytváření nebezpečných cest do nespravovaného kódu, jak je popsáno níže v části...  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Zásady vytváření názvů pro metody nespravovaného kódu  
 Navázání užitečné a velmi doporučené konvence pro pojmenování metody nespravovaného kódu. Všechny metody nespravovaného kódu jsou rozdělené do tří kategorií: **bezpečné**, **nativní**, a **unsafe**. Tato klíčová slova můžete použít jako názvy tříd v rámci které jsou definovány různé typy vstupních bodů nespravovaného kódu. Ve zdrojovém kódu by tato klíčová slova přidat k názvu třídy, jako v `Safe.GetTimeOfDay`, `Native.Xyz`, nebo `Unsafe.DangerousAPI`, např. Každý z těchto klíčových slov poskytuje informace o zabezpečení užitečné pro vývojáře, kteří používají třídy, jak je popsáno v následující tabulce.  
  
|– Klíčové slovo|Aspekty zabezpečení|  
|-------------|-----------------------------|  
|**bezpečné**|Zcela neškodné pro libovolný kód, dokonce škodlivý kód volat. Můžete použít stejně jako ostatní spravovaného kódu. Například funkci, která se získá čas, kdy je obvykle bezpečné.|  
|**nativní**|Zabezpečení jazykově neutrální; nespravovaný kód, který vyžaduje tedy nespravovaný kód oprávnění k volání. Zabezpečení je zaškrtnuto, která zastaví neoprávněného volajícího.|  
|**nezabezpečený**|Vstupní bod potenciálně nebezpečná nespravovaného kódu s zabezpečení potlačena. Vývojáři by měl použít největší opatrní při použití takových nespravovaného kódu a ujistěte se, že jiné ochrany jsou na místě, aby se zabránilo ohrožení zabezpečení. Vývojáři musí být zodpovědná, jako toto klíčové slovo přepíše systém zabezpečení.|  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
