---
title: Deklarované názvy elementu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814065"
---
# <a name="declared-element-names-visual-basic"></a>Deklarované názvy elementu (Visual Basic)
Každý element deklarovaný má název, také označovaný jako *identifikátor*, což je tento kód použije na ni odkazuje.  
  
## <a name="rules"></a>pravidla  
 Název elementu v jazyce Visual Basic musí odpovídat následujícím pravidlům:  
  
-   Musí začínat znakem abecedy nebo podtržítkem (`_`).  
  
-   Musí obsahovat jenom abecední znaky, desítkové číslice a podtržítka.  
  
-   Pokud začíná podtržítkem musí obsahovat alespoň jeden znak abecedy nebo číslici desítkové soustavy.  
  
-   Nesmí být větší než 1023 znaků.  
  
 Limit délky 1023 znaků platí také pro celý řetězec plně kvalifikovaný název, jako například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.  
  
 Následující příklad ukazuje některé názvy platný prvek.  
  
 `aB123__45`  
  
 `_567`  
  
 Následující příklad ukazuje některé názvy neplatný element. První obsahuje pouze podtržítko, druhý začíná desítková číslice a třetí obsahuje neplatný znak ($).  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  Element názvy začínající podtržítkem (`_`) nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se Specifikací CLS nemůže použít komponentu, která definuje tyto názvy. Podtržítka v jiné pozice v název elementu je však kompatibilní se Specifikací CLS.  
  
### <a name="name-length-guidelines"></a>Pokyny pro délka názvu  
 Prakticky, váš název by měl být co nejkratší při identifikaci zjevně povaze elementu. To zlepšuje čitelnost vašeho kódu a zmenší velikost řádku délku a zdrojový soubor.  
  
 Na druhé straně váš název by neměl být tak krátký, nezabývá se odpovídajícím způsobem element představuje a jak se váš kód používá. To je důležité pro čitelnost kódu. Pokud někdo jiný se snaží ho chápat, nebo pokud chcete sami se na něj dlouhou dobu, po ho napsal, můžete uložit názvy elementů vhodný značné množství času.  
  
## <a name="escaped-names"></a>Řídicí názvy  
 Obecně platí, název elementu nesmí shodují s některým z klíčových slov, jako vyhrazená v jazyce Visual Basic `Case` nebo `Friend`. Ale můžete definovat *uvozeny řídicími znaky názvu*, což je uzavřená v hranatých závorkách (`[ ]`). Uvozený uvozovacím znakem název může odpovídat všechny klíčové slovo jazyka Visual Basic, protože závorky odebrat veškerou nejednoznačnost. Použijete také závorky, při odkazování na název později ve vašem kódu.  
  
 Obecně platí, abyste používali únikové názvy pouze tehdy, když:  
  
-   Váš kód se migroval z předchozí verze jazyka Visual Basic, která není rezervovat – klíčové slovo se používá jako název; nebo  
  
-   Pracujete s kódem v jiném jazyce, ve kterém není vyhrazena daným klíčovým slovem.  
  
 V opačném případě byste měli zvážit, pokud jeho název je v konfliktu s klíčovým slovem přejmenování elementu. Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to provést. Další informace najdete v tématu [refaktoringu](/visualstudio/vb-ide/refactoring-vb).  
  
## <a name="case-sensitivity-in-names"></a>Rozlišování velikosti písmen v názvech  
 Názvy elementů v jazyce Visual Basic jsou malá a velká písmena. To znamená, že když kompilátor porovná dva názvy, které se liší abecední pouze velikostí písmen, to je interpretuje jako se stejným názvem. Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.  
  
 Ale common language runtime (CLR) používá vazbu malá a velká písmena. Proto se při vytvoření sestavení nebo knihovny DLL a ji dejte k dispozici pro jiná sestavení, názvy už nejsou velká a malá písmena. Například pokud definujete třídu s názvem elementu `ABC`, a jiných sestavení pomocí třídy přes modul common language runtime, musí odkazovat na prvek jako `ABC`. Pokud následně znovu zkompilovat vaší třídy a změňte název elementu na `abc`, ostatních sestavení pomocí vaší třídy by už přístup k prvku. Proto při uvolnění aktualizovanou verzi sestavení, byste neměli měnit abecední případ veřejné elementy.  
  
## <a name="names-and-locales"></a>Názvy a národní prostředí  
 Porovnávání názvů je nezávislý na národním prostředí. Pokud se dva názvy se shodují v jedné národní prostředí, je zaručena tak, aby odpovídaly ve všech národních prostředích.  
  
## <a name="see-also"></a>Viz také:

- [Deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [Deklarované charakteristiky elementů](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
