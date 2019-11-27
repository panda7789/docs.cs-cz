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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347310"
---
# <a name="visual-basic-naming-conventions"></a>Zásady vytváření názvů jazyka Visual Basic
Při pojmenování prvku v aplikaci Visual Basic, první znak tohoto názvu musí být abecední znak nebo podtržítko. Upozorňujeme však, že názvy začínající podtržítkem nejsou kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Následující návrhy se vztahují na pojmenování.  
  
- Zahajte každé samostatné slovo v názvu s velkým písmenem, například `FindLastRecord` a `RedrawMyForm`.  
  
- Zahajte názvy funkcí a metod pomocí příkazu, jako v `InitNameArray` nebo `CloseDialog`.  
  
- Začněte s názvy tříd, struktur, modulů a vlastností s podstatným vzhledem, jako v `EmployeeName` nebo `CarAccessory`.  
  
- Zahajte názvy rozhraní s předponou "I", za kterými následuje podstatné jméno nebo fráze na základě podstatného jména, například `IComponent`, nebo s přídavným příznakem, který popisuje chování rozhraní, jako je `IPersistable`. Nepoužívejte podtržítko a používejte zkratky bez problémů, protože zkratky můžou způsobit nejasnost.  
  
- Zahajte názvy obslužných rutin událostí s podstatným jménem, které popisují typ události a příponu "`EventHandler`", jako v "`MouseEventHandler`".  
  
- Do pole názvy tříd argumentů události zadejte příponu "`EventArgs`".  
  
- Pokud má událost koncept "před" nebo "After", používá příponu v současnosti nebo v minulosti vhodné jako v "`ControlAdd`" nebo "`ControlAdded`".  
  
- V případě dlouhých nebo často používaných podmínek používejte zkratky k udržení rozumných názvů, například "HTML" místo "jazyk HTML (Hypertext Markup Language)". Obecně platí, že názvy proměnných větší než 32 znaků jsou obtížné číst na monitoru nastaveném na nízké rozlišení. Také se ujistěte, že jsou zkratky konzistentní v celé aplikaci. Náhodné přepínání v projektu mezi "HTML" a "jazyk HTML (Hypertext Markup Language)" může vést k nejasnostem.  
  
- Vyhněte se použití názvů ve vnitřním oboru, které jsou stejné jako názvy ve vnějším oboru. Pokud je k dispozici nesprávná proměnná, může dojít k chybám. Pokud dojde ke konfliktu mezi proměnnou a klíčovým slovem se stejným názvem, je nutné identifikovat klíčové slovo před ním pomocí odpovídající knihovny typů. Například pokud máte proměnnou s názvem `Date`, můžete použít funkci vnitřní `Date` pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Klíčová slova jako názvy elementů v kódu](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
