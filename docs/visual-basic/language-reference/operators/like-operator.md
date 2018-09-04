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
ms.openlocfilehash: c5b26bd1d3ebae5136718833c124e3c6e575e9b7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537078"
---
# <a name="like-operator-visual-basic"></a>Like – operátor (Visual Basic)
Porovná řetězec oproti vzoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Žádné `Boolean` proměnné. Výsledkem je `Boolean` hodnotu, která určuje, jestli `string` splňuje požadavky `pattern`.  
  
 `string`  
 Požadováno. Žádné `String` výrazu.  
  
 `pattern`  
 Požadováno. Žádné `String` výraz vyhovující konvencím porovnávání vzorů je popsáno v "Poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota v `string` vyhovuje vzoru součástí `pattern`, `result` je `True`. Pokud řetězec nevyhovuje vzoru, `result` je `False`. Pokud mají oba `string` a `pattern` jsou prázdné řetězce, výsledkem je `True`.  
  
## <a name="comparison-method"></a>Metoda porovnání  
 Chování `Like` operátor závisí [možnost porovnat příkaz](../../../visual-basic/language-reference/statements/option-compare-statement.md). Výchozí metodu porovnání řetězce pro každý zdrojový soubor je `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Vzor možnosti  
 Předdefinovaných vzorů poskytuje univerzální nástroj pro porovnávání řetězců. Umožňují vám tak, aby odpovídaly každý znak v porovnávání vzorů funkce `string` proti konkrétní znak, zástupných znaků, seznam znak nebo rozsah znaků. V následující tabulce jsou uvedeny znaků povolených v `pattern` a aby odpovídaly.  
  
|Znaky v `pattern`|Odpovídá v `string`|  
|-----------------------------|-------------------------|  
|`?`|Libovolný znak|  
|`*`|Nula nebo více znaků|  
|`#`|Libovolné číslici (0 – 9)|  
|`[charlist]`|Libovolnému jednomu znaku v `charlist`|  
|`[!charlist]`|Libovolný znak není v `charlist`|  
  
## <a name="character-lists"></a>Znak seznamy  
 Skupina jednoho nebo více znaků (`charlist`) v závorkách (`[ ]`) slouží k odpovídá jakémukoli jednomu znaku v `string` a může obsahovat kód na téměř jakýkoli znak, včetně číslic.  
  
 Vykřičník (`!`) na začátku `charlist` znamená, že shoda se provádí v případě, že jakémukoliv znaku kromě znaků `charlist` se nachází v `string`. Při použití mimo hranaté závorky, představují vykřičník sebe sama.  
  
## <a name="special-characters"></a>Speciální znaky  
 Tak, aby odpovídaly levá závorka speciální znaky (`[`), otazník (`?`), znak (`#`) a hvězdička (`*`), uzavřete do hranatých závorek. Pravá hranatá závorka (`]`) nelze použít v rámci skupiny tak, aby odpovídaly samostatně, ale můžou se používat mimo skupinu jako jednotlivé znaky.  
  
 Sekvence znaků `[]` se považuje za řetězec nulové délky (`""`). Však nemůže být součástí seznamu znak uzavřen v závorkách. Pokud chcete zkontrolovat, jestli na umístění v `string` obsahuje nejméně jednu skupinu znaky ani žádný znak na všechny, můžete použít `Like` dvakrát. Příklad najdete v tématu [postupy: porovnání řetězce se vzorem](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Rozsahy znaků  
 Použitím spojovníku (`–`) k oddělení dolní a horní mez rozsahu, `charlist` můžete určit rozsah znaků. Například `[A–Z]` výsledků v shoda, pokud na odpovídající znak umístěte `string` obsahuje libovolný znak v rozsahu `A`–`Z`, a `[!H–L]` výsledkem shoda, pokud umístit na odpovídající znak obsahuje libovolný znak mimo rozsah `H`–`L`.  
  
 Když zadáte rozsah znaků, musí být uvedena ve vzestupném pořadí řazení, to znamená, od nejnižší a nejvyšší. Proto `[A–Z]` je platný vzor, ale `[Z–A]` není.  
  
### <a name="multiple-character-ranges"></a>Více rozsahů znaků  
 Pokud chcete zadat více rozsahů pro stejnou pozici znaku, vytvořte z nich v rámci stejné závorky bez oddělovačů. Například `[A–CX–Z]` výsledků v shoda, pokud na odpovídající znak umístěte `string` obsahuje libovolný znak buď do rozsahu `A`–`C` nebo rozsahu `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Využití spojovníku  
 Pomlčka (`–`) se mohou objevit na začátku (po vykřičník, pokud existuje) nebo na konci `charlist` tak, aby odpovídaly samotný. V jiném umístění spojovník identifikuje rozsah znaků oddělených znaky na obou stranách spojovník.  
  
## <a name="collating-sequence"></a>Pořadí řazení  
 Význam určeného rozsahu závisí na znak řazení v době běhu určeného `Option Compare` a nastavení národního prostředí systému, je kód spuštěn. S `Option Compare Binary`, rozsahu `[A–E]` odpovídá `A`, `B`, `C`, `D`, a `E`. S `Option Compare Text`, `[A–E]` odpovídá `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, a `e`. Rozsah se neshoduje s `Ê` nebo `ê` protože znaky s diakritikou kompletují za výslovnost příslušných hlásek bez znaků v pořadí řazení.  
  
## <a name="digraph-characters"></a>Digraph znaků  
 V některých jazycích jsou znaky abecedy, které představují dva samostatné znaky. Například několik jazyků použít znak `æ` k reprezentování znaky `a` a `e` Jakmile se zobrazí společně. `Like` Operátor rozpozná, že jsou ekvivalentní digraph jeden znak a dvě jednotlivých znaků.  
  
 Pokud je jazyk, který se používá znak digraph zadaný v nastavení národního prostředí systému, výskytu digraph jednoho znaku v buď `pattern` nebo `string` odpovídá sekvenci ekvivalentní dvou znaků do řetězce. Obdobně digraph znaku v `pattern` uzavřený v hranatých závorkách (samy o sobě, v seznamu nebo v rozsahu) odpovídá sekvenci ekvivalentní dvou znaků v `string`.  
  
## <a name="overloading"></a>Přetížení  
 `Like` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Like` operátor porovnání řetězců do různých vzorů. Výsledky přejít na `Boolean` označující, zda každý řetězec vyhovuje vzor proměnné.  
  
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
