---
title: Speciální znaky v kódu
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347256"
---
# <a name="special-characters-in-code-visual-basic"></a>Speciální znaky v kódu (Visual Basic)
Někdy je nutné použít ve svém kódu speciální znaky, tj. znaky, které nejsou abecední nebo číselné. Interpunkční znaménka a speciální znaky ve znakové sadě Visual Basic mají různá použití, od uspořádání textu programu k definování úkolů, které kompilátor nebo zkompilovaný program provádí. Neurčují operaci, která má být provedena.  
  
## <a name="parentheses"></a>závorky  
 Při definování procedury, například `Sub` nebo `Function`, použijte závorky. Všechny seznamy argumentů procedury musí být uzavřeny v závorkách. Můžete také použít kulaté závorky pro vložení proměnných nebo argumentů do logických skupin, zejména pro přepsání výchozího pořadí priorit operátoru ve složitém výrazu. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Po provedení předchozího kódu je hodnota `d` 8,225 a hodnota `e` je 3. Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`. Závorky ve výpočtu pro `e` přepisují výchozí prioritu.  
  
## <a name="separators"></a>Oddělovače  
 Oddělovače podle jejich názvu: oddělují oddíly kódu. V Visual Basic je znak oddělovače dvojtečkou (`:`). Oddělovače použijte, pokud chcete zahrnout více příkazů na jeden řádek místo samostatných řádků. Tím ušetříte místo a zlepšíte čitelnost kódu. Následující příklad ukazuje tři příkazy oddělené dvojtečkami.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Další informace naleznete v tématu [How to: break and kombinovat příkazy v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Znak dvojtečky (`:`) se používá také k identifikaci popisku příkazu. Další informace naleznete v tématu [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Zřetězení  
 Použijte operátor `&` pro *zřetězení*nebo propojení řetězců dohromady. Nepleťte si ho s operátorem `+`, který přidá dohromady číselné hodnoty. Použijete-li operátor `+` k zřetězení při práci s číselnými hodnotami, můžete získat nesprávné výsledky. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Po provedení předchozího kódu je hodnota `resultA` 21,01 a hodnota `resultB` je "10,0111".  
  
## <a name="member-access-operators"></a>Operátory přístupu členů  
 Chcete-li získat přístup ke členu typu, použijte operátor tečka (`.`) nebo vykřičník (`!`) mezi názvem typu a názvem člena.  
  
### <a name="dot--operator"></a>Tečka (.) Podnikatel  
 Použijte operátor `.` pro třídu, strukturu, rozhraní nebo výčet jako operátor přístupu členů. Členem může být pole, vlastnost, událost nebo metoda. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Vykřičník (!) Podnikatel  
 Operátor `!` použijte pouze pro třídu nebo rozhraní jako operátor přístupu ke slovníku. Třída nebo rozhraní musí mít výchozí vlastnost, která přijímá jeden `String` argument. Identifikátor hned za operátorem `!` se bude hodnotou argumentu předanou výchozí vlastnosti jako řetězec. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Tři výstupní řádky `MsgBox` všechny zobrazují `32856`hodnoty. První řádek používá tradiční přístup k vlastnosti `index`, druhá využívá fakt, že `index` je výchozí vlastnost `hasDefault`třídy a třetí používá slovník přístup ke třídě.  
  
 Všimněte si, že druhý operand operátoru `!` musí být platný identifikátor Visual Basic, který není uzavřen do dvojitých uvozovek (`" "`). Jinými slovy, nelze použít řetězcový literál nebo řetězcovou proměnnou. Následující změna na poslední řádek `MsgBox` volání vygeneruje chybu, protože `"X"` je uzavřený řetězcový literál.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Odkazy na výchozí kolekce musí být explicitní. Konkrétně nelze použít operátor `!` pro proměnnou s pozdní vazbou.  
  
 `!` znak se používá také jako znak `Single` typu.  
  
## <a name="see-also"></a>Viz také:

- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
