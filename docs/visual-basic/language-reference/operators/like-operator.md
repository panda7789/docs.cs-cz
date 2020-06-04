---
title: Like – operátor
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
ms.openlocfilehash: 4279d90c74c80403146448a8ba5a6051ec9d12f6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401550"
---
# <a name="like-operator-visual-basic"></a>Like – operátor (Visual Basic)
Porovná řetězec se vzorem.  

> [!IMPORTANT]
> `Like`Operátor není aktuálně podporován v projektech .NET Core a .NET Standard.

## <a name="syntax"></a>Syntaxe  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Libovolná `Boolean` Proměnná. Výsledkem je hodnota, `Boolean` která označuje, zda `string` vyhovuje `pattern` .  
  
 `string`  
 Povinná hodnota. Libovolný `String` výraz.  
  
 `pattern`  
 Povinná hodnota. Libovolný `String` výraz, který odpovídá konvencím porovnávání vzorů popsaným v části "poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota v `string` splňuje vzor obsažený v `pattern` , `result` je `True` . Pokud řetězec nevyhovuje vzoru, `result` je `False` . Pokud `string` jsou a i `pattern` prázdné řetězce, výsledek je `True` .  
  
## <a name="comparison-method"></a>Metoda porovnání  
 Chování `Like` operátora závisí na [příkazu Option Compare](../statements/option-compare-statement.md). Výchozí metoda porovnání řetězců pro každý zdrojový soubor je `Option Compare Binary` .  
  
## <a name="pattern-options"></a>Možnosti vzorku  
 Předdefinované porovnávání vzorů poskytuje univerzální nástroj pro porovnávání řetězců. Funkce porovnávání se vzorci vám umožní porovnat jednotlivé znaky s `string` konkrétním znakem, zástupným znakem, seznamem znaků nebo rozsahem znaků. V následující tabulce jsou uvedeny znaky, které `pattern` jsou povolené v a co se shodují.  
  
|Znaky v`pattern`|Shody v`string`|  
|-----------------------------|-------------------------|  
|`?`|Libovolný jeden znak|  
|`*`|Nula nebo více znaků|  
|`#`|Jakákoli jedna číslice (0 – 9)|  
|`[charlist]`|Libovolný jeden znak v`charlist`|  
|`[!charlist]`|Libovolný jeden znak, který není v`charlist`|  
  
## <a name="character-lists"></a>Seznamy znaků  
 Skupina jednoho nebo více znaků ( `charlist` ) uzavřená v závorkách ( `[ ]` ) se dá použít k porovnávání libovolného jednotlivého znaku v `string` a může obsahovat skoro jakýkoli kód znaku, včetně číslic.  
  
 Vykřičník ( `!` ) na začátku `charlist` znamená, že je provedena shoda, pokud libovolný znak kromě znaků v `charlist` je nalezen v `string` . Při použití mimo hranaté závorky se vykřičník shoduje.  
  
## <a name="special-characters"></a>Speciální znaky  
 Chcete-li najít shodu se speciálními znaky, levou hranatou závorku ( `[` ), otazníkem ( `?` ), číslem znaménkem ( `#` ) a hvězdičkou ( `*` ), vložte je do závorek. Pravou hranatou závorku ( `]` ) nelze použít v rámci skupiny, aby se shodovala se sebou, ale lze ji použít mimo skupinu jako jednotlivý znak.  
  
 Sekvence znaků `[]` je považována za řetězec s nulovou délkou ( `""` ). Nemůže však být součástí seznamu znaků uzavřený v závorkách. Pokud chcete zjistit, zda pozice v umístění `string` obsahuje jednu ze skupin znaků nebo žádný znak vůbec, můžete použít `Like` dvakrát. Příklad naleznete v tématu [How to: Match String to a vzor](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Rozsahy znaků  
 Použitím spojovníku ( `–` ) k oddělení dolních a horních mezí rozsahu `charlist` lze určit rozsah znaků. Výsledkem je například `[A–Z]` shoda, pokud odpovídající pozice znaku v `string` poli obsahuje libovolný znak v rozsahu `A` – `Z` a výsledkem je shoda, `[!H–L]` Pokud odpovídající pozice znaku obsahuje libovolný znak mimo rozsah `H` – `L` .  
  
 Když zadáte rozsah znaků, musí být ve vzestupném pořadí řazení, tj. od nejnižší po nejvyšší. Proto `[A–Z]` je platný vzor, ale není `[Z–A]` .  
  
### <a name="multiple-character-ranges"></a>Více rozsahů znaků  
 Chcete-li zadat více rozsahů pro stejné umístění znaků, vložte je do stejné hranaté závorky bez oddělovačů. Výsledkem je například `[A–CX–Z]` shoda, pokud odpovídající pozice znaku v `string` části obsahuje libovolný znak v rámci rozsahu `A` `C` nebo rozsahu `X` – `Z` .  
  
### <a name="usage-of-the-hyphen"></a>Použití pomlčky  
 Spojovník ( `–` ) se může objevit buď na začátku (za vykřičníkem, pokud existuje), nebo na konci `charlist` pro vyhledání sebe sama. V jakémkoli jiném umístění pomlčka identifikuje rozsah znaků oddělených znaky na obou stranách pomlčky.  
  
## <a name="collating-sequence"></a>Sekvence řazení  
 Význam zadaného rozsahu závisí na řazení znaků v době běhu, podle určení `Option Compare` a nastavení národního prostředí systému, na kterém je spuštěný kód. S `Option Compare Binary` , rozsah `[A–E]` odpovídá,,, `A` `B` `C` `D` a `E` . With `Option Compare Text` , `[A–E]` Matches,, `A` `a` `À` , `à` , `B` , `b` , `C` , `c` , `D` , `d` , a `E` `e` . Rozsah neodpovídá `Ê` nebo `ê` vzhledem k tomu, že znaky zvýrazněné v pořadí řazení jsou vyrovnávány po nezvýrazněných znacích.  
  
## <a name="digraph-characters"></a>Znaky grafu  
 V některých jazycích existují abecední znaky, které představují dva samostatné znaky. Například několik jazyků používá znak `æ` k reprezentaci znaků `a` a `e` když se zobrazí společně. `Like`Operátor rozpozná, že jediný znak v grafu a dva jednotlivé znaky jsou ekvivalentní.  
  
 Pokud je v nastavení národního prostředí systému určen jazyk, který používá znak rozgrafu, je výskyt jednoho znaku grafu v buď `pattern` nebo `string` stejný jako ekvivalentní sekvence dvou znaků v druhém řetězci. Podobně znak v grafu `pattern` uzavřený v závorkách (sám o sobě, v seznamu nebo v rozsahu) odpovídá ekvivalentní posloupnosti dvou znaků v `string` .  
  
## <a name="overloading"></a>Přetížení  
 `Like`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `Like` operátor k porovnání řetězců s různými vzory. Výsledky se přejdou do `Boolean` proměnné, která označuje, jestli každý řetězec vyhovuje vzoru.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [Operátory porovnání](comparison-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Option Compare – příkaz](../statements/option-compare-statement.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Postupy: Porovnání řetězce se vzorem](../../programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
