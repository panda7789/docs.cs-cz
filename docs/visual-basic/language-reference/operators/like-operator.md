---
title: Like – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: a9c672a397510c69c9ee67358689feff80d8831a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605417"
---
# <a name="like-operator-visual-basic"></a>Like – operátor (Visual Basic)
Porovnání řetězce se vzorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` proměnné. Výsledkem je, `Boolean` hodnotu, která určuje, jestli `string` splňuje požadavky `pattern`.  
  
 `string`  
 Požadováno. Všechny `String` výraz.  
  
 `pattern`  
 Požadováno. Všechny `String` výraz, který odpovídá se porovnávání názvů popsané v "Poznámky."  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota v `string` splňuje vzoru obsažené v `pattern`, `result` je `True`. Pokud řetězec nevyhovuje vzoru, `result` je `False`. Pokud oba `string` a `pattern` jsou prázdné řetězce, výsledkem je `True`.  
  
## <a name="comparison-method"></a>Metoda porovnání  
 Chování `Like` operátor závisí na [Option Compare – příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md). Je výchozí metodou porovnání řetězce pro každý zdrojový soubor `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Vzor možnosti  
 Shoda vzoru předdefinované poskytuje univerzální nástroj pro porovnání řetězců. Funkce porovnávání umožňují odpovídat každý znak v `string` proti konkrétní znak, zástupný znak, seznamu znaků nebo rozsah znaků. V následující tabulce jsou uvedeny povolených znaků v `pattern` a budou odpovídat.  
  
|Znaků. `pattern`|Odpovídá v `string`|  
|-----------------------------|-------------------------|  
|`?`|Libovolný znak|  
|`*`|Žádný nebo více znaků|  
|`#`|Všechny jednu číslici (0 – 9)|  
|`[charlist]`|Libovolný znak v `charlist`|  
|`[!charlist]`|Libovolný znak není v `charlist`|  
  
## <a name="character-lists"></a>Znak zobrazí  
 Skupinu jeden nebo více znaků (`charlist`) uzavřeny do hranatých závorek (`[ ]`) lze nahradit libovolný znak v `string` a může obsahovat téměř jakoukoli znak kód, včetně číslic.  
  
 S vykřičníkem (`!`) na začátku `charlist` znamená, že shoda se provádí v případě, že všechny znak s výjimkou znaků v `charlist` se nachází v `string`. Při použití mimo závorky, odpovídá vykřičník sám sebe.  
  
## <a name="special-characters"></a>Speciální znaky  
 Tak, aby odpovídaly speciální znaky levou hranatou závorku (`[`), otazník (`?`), počet přihlášení (`#`) a znak hvězdičky (`*`), uzavřete je do hranatých závorek. Pravou hranatou závorku (`]`) nelze použít v rámci skupiny tak, aby odpovídaly samostatně, ale dá se používat mimo skupinu jako samostatný znak.  
  
 Posloupnost znaků `[]` se považuje za řetězec nulové délky (`""`). Však nemůže být součástí seznam znak v závorkách. Pokud chcete zkontrolovat, zda pozice v `string` obsahuje jednu skupinu znaky ani žádný znak na všechny, můžete použít `Like` dvakrát. Příklad, naleznete v části [postupy: porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Rozsahy znaků  
 Použitím spojovníku (`–`) oddělit dolní i horní hranici rozsahu, `charlist` můžete zadat rozsah znaků. Například `[A–Z]` výsledkem shody, pokud odpovídající znaku pozice v `string` obsahuje libovolný znak v rozsahu `A`–`Z`, a `[!H–L]` výsledků v shody, pokud odpovídající znaku pozice libovolný znak mimo rozsah obsahuje `H`–`L`.  
  
 Když zadáte rozsah znaků, musí se zobrazí ve vzestupném pořadí řazení, který je od nejnižší a nejvyšší. Proto `[A–Z]` je platný vzor, ale `[Z–A]` není.  
  
### <a name="multiple-character-ranges"></a>Více rozsahům znak  
 Pokud chcete zadat víc rozsahů pro stejné pozice znaku, jejich umístění v rámci stejné závorky bez oddělovačů. Například `[A–CX–Z]` výsledkem shody, pokud odpovídající znaku pozice v `string` obsahuje libovolný znak buď rozsahu `A`–`C` nebo rozsahu `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Využití spojovník  
 Pomlčka (`–`) můžete zobrazit na začátku (po s vykřičníkem, pokud existuje) nebo na konci `charlist` tak, aby odpovídaly sám sebe. V jiném umístění určuje pomlčka rozsah znaků, které jsou odděleny znaky na obou stranách spojovník.  
  
## <a name="collating-sequence"></a>Pořadí řazení  
 Význam zadaný rozsah závisí na znak řazení v době běhu určeného `Option``Compare` a nastavení národního prostředí systému kód běží na. S `Option``Compare``Binary`, rozsahu `[A–E]` odpovídá `A`, `B`, `C`, `D`, a `E`. S `Option``Compare``Text`, `[A–E]` odpovídá `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, a `e`. Rozsah neodpovídá `Ê` nebo `ê` protože znaky s diakritikou collate po příslušných znaků v pořadí řazení.  
  
## <a name="digraph-characters"></a>Spřežka znaků  
 V některých jazycích jsou znaky abecedy, které představují dva samostatné znaky. Například několik jazyků použít znak `æ` představují znaky `a` a `e` Jakmile se zobrazí společně. `Like` Operátor rozpozná, že spřežka jeden znak a dva jednotlivé znaky jsou ekvivalentní.  
  
 Když je jazyk, který používá znak spřežka zadaný v nastavení národního prostředí systému, výskytu jedné spřežka znaku buď `pattern` nebo `string` odpovídá ekvivalentní pořadí dvou znaků v další řetězec. Podobně spřežka znak v `pattern` v závorkách (samy o sobě, v seznamu, nebo v rozsahu) odpovídá ekvivalentní pořadí dvou znaků v `string`.  
  
## <a name="overloading"></a>Přetížení  
 `Like` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Like` operátor pro porovnání řetězců do různých vzorů. Výsledky přejděte do `Boolean` proměnné, která určuje, zda každý řetězec splňuje vzoru.  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Postupy: Porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
