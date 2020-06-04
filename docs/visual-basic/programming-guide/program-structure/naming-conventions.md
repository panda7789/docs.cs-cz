---
title: Konvence vytváření názvů
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398341"
---
# <a name="visual-basic-naming-conventions"></a>Zásady vytváření názvů jazyka Visual Basic
Při pojmenování prvku v aplikaci Visual Basic, první znak tohoto názvu musí být abecední znak nebo podtržítko. Upozorňujeme však, že názvy začínající podtržítkem nejsou kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Následující návrhy se vztahují na pojmenování.  
  
- Zahajte každé samostatné slovo v názvu s velkým písmenem, jako v `FindLastRecord` a `RedrawMyForm` .  
  
- Začněte s názvy funkcí a metod pomocí příkazu, jako v `InitNameArray` nebo `CloseDialog` .  
  
- Začněte s názvy tříd, struktur, modulů a vlastností s podstatným vzhledem, jako v `EmployeeName` nebo `CarAccessory` .  
  
- Zahajte názvy rozhraní s předponou "I", za kterými následuje podstatné jméno nebo fráze na základě podstatného jména, například `IComponent` nebo s přídavným znakem, který popisuje chování rozhraní, jako je `IPersistable` . Nepoužívejte podtržítko a používejte zkratky bez problémů, protože zkratky můžou způsobit nejasnost.  
  
- Zahajte názvy obslužných rutin událostí s podstatným jménem, které popisují typ události a `EventHandler` příponu "" jako v " `MouseEventHandler` ".  
  
- Do pole názvy tříd argumentů události přidejte `EventArgs` příponu "".  
  
- Pokud má událost koncept "před" nebo "After", používá příponu v současnosti nebo v minulosti vhodné jako v " `ControlAdd` " nebo " `ControlAdded` ".  
  
- V případě dlouhých nebo často používaných podmínek používejte zkratky k udržení rozumných názvů, například "HTML" místo "jazyk HTML (Hypertext Markup Language)". Obecně platí, že názvy proměnných větší než 32 znaků jsou obtížné číst na monitoru nastaveném na nízké rozlišení. Také se ujistěte, že jsou zkratky konzistentní v celé aplikaci. Náhodné přepínání v projektu mezi "HTML" a "jazyk HTML (Hypertext Markup Language)" může vést k nejasnostem.  
  
- Vyhněte se použití názvů ve vnitřním oboru, které jsou stejné jako názvy ve vnějším oboru. Pokud je k dispozici nesprávná proměnná, může dojít k chybám. Pokud dojde ke konfliktu mezi proměnnou a klíčovým slovem se stejným názvem, je nutné identifikovat klíčové slovo před ním pomocí odpovídající knihovny typů. Například pokud máte proměnnou s názvem `Date` , můžete použít vnitřní `Date` funkci pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- [Klíčová slova jako názvy elementů v kódu](keywords-as-element-names-in-code.md)
- [Me, My, MyBase a MyClass](me-my-mybase-and-myclass.md)
- [Deklarované názvy elementů](../language-features/declared-elements/declared-element-names.md)
- [Struktura programu a konvence kódu](program-structure-and-code-conventions.md)
- [Reference jazyka Visual Basic](../../language-reference/index.md)
