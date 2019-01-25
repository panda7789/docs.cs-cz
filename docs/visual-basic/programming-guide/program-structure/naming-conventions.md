---
title: Zásady vytváření názvů jazyka Visual Basic
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
ms.openlocfilehash: ebb9d21e32993f2eb035993d32dc3de7d97b49f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672133"
---
# <a name="visual-basic-naming-conventions"></a>Zásady vytváření názvů jazyka Visual Basic
Pokud název elementu v aplikaci Visual Basic, první znak s tímto názvem musí být abecední znak nebo podtržítko. Upozorňujeme, že názvy začínající podtržítkem jsou nekompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Následující doporučení platí pro pojmenování.  
  
-   Začněte všech samostatných slov v názvu s velkým písmenem, stejně jako v `FindLastRecord` a `RedrawMyForm`.  
  
-   Začněte názvy funkce a metody s operací, jako v `InitNameArray` nebo `CloseDialog`.  
  
-   Začněte třída, struktura, modul a názvy vlastností s podstatné jméno, stejně jako v `EmployeeName` nebo `CarAccessory`.  
  
-   Začněte názvy rozhraní s předponou "I", za nímž následuje podstatné jméno nebo fráze podstatné jméno, jako je třeba `IComponent`, nebo s přídavné popisující chování rozhraní, jako je třeba `IPersistable`. Nepoužívají podtržítko a zkratky používejte opatrně, protože zkratky, může způsobit zmatení.  
  
-   Názvy obslužných rutin událostí začínat podstatné jméno popisující typ události, za nímž následuje "`EventHandler`"příponu, například"`MouseEventHandler`".  
  
-   V názvech tříd argument události, zahrnout "`EventArgs`" příponu.  
  
-   Pokud událost obsahuje koncept "before" nebo "after", je nutné použít příponu v přítomný a minulý čas, stejně jako v "`ControlAdd`"nebo"`ControlAdded`".  
  
-   Dlouhé nebo často používané termíny použijte zkratky zachovat název délky přiměřenou, například "HTML" místo "Jazyk HTML". Obecně jsou delší než 32 znaků. názvy proměnných mohou ztížit čtení na monitoru nastavit s nízkým rozlišením. Také ujistěte se, že vaše zkratky jsou konzistentní vzhledem k aplikacím v celé aplikaci. V projektu mezi "HTML" a "Jazyk" náhodně přepínání může vést k nejasnostem.  
  
-   Nepoužívejte názvy ve vnitřním oboru, které jsou stejné jako názvy ve vnějším oboru. K chybám může dojít, pokud nesprávné proměnnou přistupuje. Pokud dojde ke konfliktu mezi proměnnou a klíčové slovo se stejným názvem, je nutné určit klíčového slova před s knihovnou příslušného typu. Například, pokud máte proměnnou s názvem `Date`, můžete použít vnitřní objekt `Date` funkce pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:
- [Klíčová slova jako názvy elementů v kódu](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [Me, My, MyBase a MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)
