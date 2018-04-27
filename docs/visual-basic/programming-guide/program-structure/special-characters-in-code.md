---
title: Speciální znaky v kódu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b724c48320f74045d7192be6d6e269c00511ffc9
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="special-characters-in-code-visual-basic"></a>Speciální znaky v kódu (Visual Basic)
Někdy je nutné použít speciální znaky v kódu, který je znaků, které nejsou abecední nebo číselný. Interpunkce a speciální znaky znakové sady Visual Basic mají různé používá z uspořádání program text, který má definice úlohy, které provádí kompilátor nebo zkompilovaný program. Nezadávejte provést operaci.  
  
## <a name="parentheses"></a>Závorky  
 Závorky lze použít, když definujete postup, například `Sub` nebo `Function`. Všechny seznamy argumentů postupu je nutné uzavřít do závorek. Také pomocí závorek pro umístění proměnné nebo argumenty do logických skupin, zejména přepsat výchozí pořadí operátorů v složitý výraz. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Provedení předchozí kódu hodnotu `d` 8.225 a hodnota `e` je 3. Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní `d = b + (c / a)`. Závorky při výpočtu `e` změnit výchozí prioritu.  
  
## <a name="separators"></a>Oddělovače  
 Oddělovače udělat, co navrhuje jména: oddělit sekcí kódu. V jazyce Visual Basic znak oddělovače je dvojtečkou (`:`). Oddělovače použijte, pokud chcete zahrnout více příkazů na jeden řádek místo samostatné řádky. Tím ušetříte místo a zlepšuje čitelnost kódu. Následující příklad ukazuje tři příkazy oddělené dvojtečkou.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Další informace najdete v tématu [postupy: přerušení a kombinace příkazů v kódu](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 Dvojtečkou (`:`) znak slouží také k identifikaci příkaz štítek. Další informace najdete v tématu [postup: příkazy popisek](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Zřetězení  
 Použití `&` operátor pro *zřetězení*, nebo společně propojení řetězce. Nepleťte si její `+` operátor, který přidá společně číselné hodnoty. Pokud použijete `+` operátor ke zřetězení při pracovat na číselné hodnoty, můžete získat nesprávné výsledky. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Provedení předchozí kódu hodnotu `resultA` 21.01 a hodnota `resultB` je "10.0111".  
  
## <a name="member-access-operators"></a>Operátory pro přístup ke člena  
 O přístup člena typu, použijte tečky (`.`) nebo vykřičník (`!`) operátor mezi název typu a název člena.  
  
### <a name="dot--operator"></a>Tečku (.) Operátor  
 Použití `.` operátor na třídy, struktury, rozhraní nebo výčtu jako operátor přístupu členů. Člen může být pole, vlastnosti, události nebo metody. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Vykřičník (!) Operátor  
 Použití `!` operátor pouze na třídy nebo rozhraní jako operátor přístupu slovníku. Třídy nebo rozhraní musí mít výchozí vlastnosti, která přijímá jeden `String` argument. Identifikátor hned `!` operátor stane hodnota argumentu předaného proměnné výchozí vlastnosti jako řetězec. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Jsou tři výstup řádků `MsgBox` všechny zobrazit hodnotu `32856`. První řádek používá tradiční přístup k vlastnosti `index`, druhý využívá fakt, který `index` je výchozí vlastnost třídy `hasDefault`, a třetí používá slovníkový přístup ke třídě.  
  
 Všimněte si, že druhý operand `!` operátor musí být platný identifikátor jazyka Visual Basic není uzavřena v uvozovkách (`" "`). Jinými slovy nemůžete použít řetězcový literál nebo proměnná řetězce. Následující změnit na poslední řádek `MsgBox` volání vygeneruje chybu, protože `"X"` nachází závorkách řetězcový literál.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Odkazy na výchozích kolekcí musí být explicitní. Konkrétně nelze použít `!` operátor na proměnnou pozdní vazbu.  
  
 `!` Znak se používá jako `Single` zadávat znaky.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu a zásady týkající se kódu](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
