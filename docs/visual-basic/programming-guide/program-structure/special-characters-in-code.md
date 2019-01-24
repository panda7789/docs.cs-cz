---
title: Speciální znaky v kódu (Visual Basic)
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
ms.openlocfilehash: 1541ac1793c9f3c082b688fecd4eb82fb5b59590
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726725"
---
# <a name="special-characters-in-code-visual-basic"></a>Speciální znaky v kódu (Visual Basic)
Někdy je nutné použít speciální znaky v kódu, to znamená, znaky, které nejsou čísla. Interpunkce a speciální znaky znakové sady Visual Basic mají různé možnosti použití, z uspořádání textu programu k definování úkolů, které kompilátor nebo zkompilovaný program provede. Nezadávejte operaci, která se má provést.  
  
## <a name="parentheses"></a>Závorky  
 Používejte závorky definuje proceduru, třeba `Sub` nebo `Function`. Všechny seznamy argumentů postupu je nutné uzavřít do závorek. Také při použití závorek k uvedení proměnných nebo argumentů do logických skupin, zejména pro přepsání výchozí pořadí podle priority operátoru ve výrazu komplexní. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Po spuštění předchozího kódu, hodnota `d` je 8.225 a hodnota `e` je 3. Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`. Závorky ve výpočtu pro `e` změnit výchozí prioritu.  
  
## <a name="separators"></a>Oddělovače  
 Oddělovače udělat, co jejich název napovídá: oddělují části kódu. V jazyce Visual Basic je oddělovací znak dvojtečky (`:`). Používejte oddělovače, při které chcete zahrnout více příkazů na jednom řádku namísto samostatné řádky. To šetří místo a zlepšuje čitelnost kódu. Následující příklad ukazuje tři příkazy, které jsou odděleny dvojtečkami.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Další informace najdete v tématu [jak: Přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Dvojtečka (`:`) znaků se také používá k identifikaci popisek příkazu. Další informace najdete v tématu [jak: Vytváření popisků příkazů](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Zřetězení  
 Použití `&` operátor pro *zřetězení*, nebo propojení řetězce. Nepleťte si jej `+` operátor, který přidá společně číselné hodnoty. Pokud používáte `+` operátor zřetězení při pracovat na číselné hodnoty, můžete získat nesprávné výsledky. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Po spuštění předchozího kódu, hodnota `resultA` 21.01 a hodnota `resultB` je "10.0111".  
  
## <a name="member-access-operators"></a>Operátory přístupu členů  
 Chcete-li přístup ke členu typu, použijte tečku (`.`) nebo vykřičník (`!`) – operátor mezi název typu a název člena.  
  
### <a name="dot--operator"></a>Tečka (.) Operátor  
 Použití `.` operátor na třídu, strukturu, rozhraní nebo výčet jako operátor přístupu členů. Člen může být pole, vlastnosti, události nebo metody. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Vykřičník (!) Operátor  
 Použití `!` operátor pouze pro třídu nebo rozhraní jako slovník – operátor přístupu. Třída nebo rozhraní musí mít výchozí vlastnost, která přijímá jeden `String` argument. Identifikátor hned za `!` operátor stane hodnota argumentu předaného výchozí vlastnosti jako řetězec proměnné. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Tři výstupní řádky `MsgBox` všechny zobrazit hodnotu `32856`. První řádek využívá tradiční přístup k vlastnosti `index`, druhý používá faktu, který `index` je výchozí vlastnost třídy `hasDefault`, a třetí použije slovníkový přístup ke třídě.  
  
 Všimněte si, že druhý operand `!` operator musí být platným identifikátorem jazyka Visual Basic není uzavřen do dvojitých uvozovek (`" "`). Jinými slovy nelze použít textový literál nebo proměnná řetězce. Následující změnit na poslední řádek `MsgBox` volání dojde k chybě, protože `"X"` je uzavřené řetězec literálu.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Odkazy na výchozích kolekcí musí být explicitní. Zejména, nelze použít `!` operátor u proměnné s pozdní vazbou.  
  
 `!` Znak slouží také jako `Single` znak.  
  
## <a name="see-also"></a>Viz také:
- [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
