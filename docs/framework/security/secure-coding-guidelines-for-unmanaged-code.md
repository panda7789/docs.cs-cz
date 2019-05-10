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
ms.openlocfilehash: 59a25eb9b854f0f303d8b1d97db40406c2818df8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626281"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Pokyny pro zabezpečení nespravovaného kódu
Kód knihovny je potřeba volat nespravovaný kód (například nativního kódu rozhraní API, jako například Win32). Protože to znamená, že přejdete mimo zónu zabezpečení pro spravovaný kód, kvůli upozornění je povinný. Pokud váš kód je nezávislá na zabezpečení, kódu a jakýkoli kód, který volá musí mít povolení pro nespravovaný kód (<xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> příznak zadán).  
  
 Často je ale nepřiměřené pro vaše volající tyto výkonné oprávnění. V takových případech může být důvěryhodný kód prostředník, podobně jako spravované obálky nebo podle kód knihovny [zabezpečení kódu obálky](../../../docs/framework/misc/securing-wrapper-code.md). Pokud základní funkce nespravovaného kódu je zcela bezpečné, ji můžou přímo zveřejnit; v opačném případě vhodná oprávnění (požadavek) je vyžadována kontrola nejprve.  
  
 Pokud váš kód volá nespravovaný kód, ale nechcete vyžadují vaši volající mít dostatečná oprávnění pro přístup k nespravovanému kódu, musíte vyhodnotit tato práva. Kontrolní výraz zablokuje procházení zásobníku na rámce. Musíte být opatrní vytvořit bezpečnostní riziko v tomto procesu. Obvykle to znamená, že musí vyžadují vhodná oprávnění od volajících a následně pomocí nespravovaného kódu provádět pouze umožňuje toto oprávnění a žádné další. V některých případech (například funkce denní dobu get) může být nespravovaný kód přímo vystavena volající bez žádné bezpečnostní kontroly. Veškerý kód, který se vyhodnotí v každém případě musí nést odpovědnost za zabezpečení.  
  
 Vzhledem k tomu, že spravovaný kód, který poskytuje cestu kódu do nativního kódu je potenciální cíle škodlivý kód, určující, které nespravovaného kódu může být bezpečně používán a jak musí být použit vyžaduje extreme péči. Obecně platí nespravovaného kódu by nikdy být přímo vystavený částečně důvěryhodné volající. Existují dva primární aspekty při hodnocení zabezpečení nespravovaného kódu pomocí knihoven, které jsou volány částečně důvěryhodným kódem:  
  
- **Funkce**. Nespravované rozhraní API poskytuje funkce, které nepovoluje volající provádět potenciálně nebezpečná operace? Zabezpečení přístupu kódu používá oprávnění vynutit přístup k prostředkům, takže zvažte, jestli rozhraní API používá soubory, uživatelské rozhraní, nebo práce s vlákny, nebo zda poskytuje chráněné informace. Pokud ano, musí obalování spravovaného kódu dříve, než ho zadat vyžadují potřebná oprávnění. Kromě toho při nechrání oprávnění, musí být přístup do paměti omezeny na přísnou bezpečnost typů.  
  
- **Kontroluje se parametr**. Běžné útoku pass neočekávané parametry do vystavených metody nespravovaného kódu rozhraní API za účelem způsobit, že provoz z specifikace. Přetečení vyrovnávací paměti pomocí index mimo rozsah nebo hodnoty posunu jsou obvyklým příkladem tento typ útoku, jako jsou všechny parametry, které může zneužít chybu v základní kód. Proto i v případě nespravovaného kódu rozhraní API je funkčně bezpečné (po nezbytné požadavky) pro částečně důvěryhodné volající, spravovaný kód musí také kontrolu platnosti parametru vyčerpávajícím způsobem zajistit, že žádné nežádoucí volání jsou z škodlivý kód pomocí managed kód obálky vrstvy.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Používání atributu SuppressUnmanagedCodeSecurityAttribute  
 Existuje aspekt výkonu uplatnění a následným voláním nespravovaného kódu. Systém zabezpečení pro každé volání, se automaticky požadavky oprávnění nespravovaného kódu, což vede k procházení zásobníku pokaždé, když. Pokud vyhodnocujete a okamžitě volat nespravovaný kód, může být procházení zásobníku nemá význam: skládá se z vašeho kontrolní výraz a volání nespravovaného kódu.  
  
 Vlastní atribut volá <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> lze použít u nespravovaného kódu vstupní body k vypnutí běžná bezpečnostní kontroly, která požaduje <xref:System.Security.Permissions.SecurityPermission> s <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> zadané oprávnění. Extrémně opatrní musí být provedeny vždy, když to, protože tato akce vytvoří otevřené dveře do nespravovaného kódu se modul runtime zabezpečení kontroluje. Je třeba poznamenat, i s **SuppressUnmanagedCodeSecurityAttribute** použít, je jednorázová kontrola zabezpečení, ke které dochází během kompilace just-in-time (JIT) a ujistěte se, že bezprostředního volajícího mají oprávnění k volání nespravovaný kód.  
  
 Pokud používáte **SuppressUnmanagedCodeSecurityAttribute**, zkontrolujte následující body:  
  
- Zkontrolujte vstupní bod nespravovaného kódu, interní nebo jinak nedostupná mimo váš kód.  
  
- Každé volání nespravovaného kódu je potenciální bezpečnostní riziko. Ujistěte se, že váš kód není na portálu pro škodlivý kód nepřímo volat nespravovaný kód a vyhnout se kontrola zabezpečení. Požadovat oprávnění, v případě potřeby.  
  
- Můžete explicitně určit při vytváření nebezpečné cestu do nespravovaného kódu, jak je popsáno níže v části zásady vytváření názvů...  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Zásady vytváření názvů pro metody nespravovaného kódu  
 Vytvořilo se použitelné a vysoce doporučené konvence pro pojmenovávání metody nespravovaného kódu. Všechny metody nespravovaného kódu jsou rozdělené do tří kategorií: **bezpečné**, **nativní**, a **nebezpečné**. Tato klíčová slova můžete použít jako názvy tříd, ve kterém jsou definovány různé typy vstupních bodů nespravovaného kódu. Ve zdrojovém kódu by tato klíčová slova přidat k názvu třídy jako v `Safe.GetTimeOfDay`, `Native.Xyz`, nebo `Unsafe.DangerousAPI`, např. Každá z těchto klíčových slov poskytuje zabezpečení užitečné informace pro vývojáře, kteří používají tuto třídu, jak je popsáno v následující tabulce.  
  
|Klíčové slovo|Důležité informace o zabezpečení|  
|-------------|-----------------------------|  
|**safe**|Zcela neškodný pro libovolný kód, dokonce i škodlivý kód pro volání. Můžete použít stejně jako ostatní spravovaného kódu. Například funkce, která získá denní dobu, je obvykle bezpečné.|  
|**Nativní**|Zabezpečení – neutrální; To znamená nespravovaný kód, který vyžaduje nespravovaný kód oprávnění k volání. Zabezpečení je zaškrtnuto, které zastaví neoprávněného volajícího.|  
|**unsafe**|Vstupní bod nespravovaného kódu potenciálně nebezpečné se zabezpečením potlačena. Vývojáři by měl použít nejvyšší opatrností při použití těchto nespravovaného kódu, ujistěte se, že dalších způsobů ochrany jsou na místě, aby se zabránilo ohrožení zabezpečení. Vývojáři musí být zodpovědná, jak toto klíčové slovo přepíše zabezpečení systému.|  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
