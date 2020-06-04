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
ms.openlocfilehash: c9b170ed812474cdeee100f1dc388d5c7e85f2cc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400588"
---
# <a name="special-characters-in-code-visual-basic"></a>Speciální znaky v kódu (Visual Basic)
Někdy je nutné použít ve svém kódu speciální znaky, tj. znaky, které nejsou abecední nebo číselné. Interpunkční znaménka a speciální znaky ve znakové sadě Visual Basic mají různá použití, od uspořádání textu programu k definování úkolů, které kompilátor nebo zkompilovaný program provádí. Neurčují operaci, která má být provedena.  
  
## <a name="parentheses"></a>Závorky  
 Při definování procedury, jako je například nebo, použijte závorky `Sub` `Function` . Všechny seznamy argumentů procedury musí být uzavřeny v závorkách. Můžete také použít kulaté závorky pro vložení proměnných nebo argumentů do logických skupin, zejména pro přepsání výchozího pořadí priorit operátoru ve složitém výrazu. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Po provedení předchozího kódu se jedná o hodnotu `d` 8,225 a hodnota `e` je 3. Výpočet pro `d` používá výchozí prioritu `/` přes `+` a je ekvivalentní s `d = b + (c / a)` . Závorky ve výpočtu pro `e` přepsání výchozí priority.  
  
## <a name="separators"></a>Oddělovače  
 Oddělovače podle jejich názvu: oddělují oddíly kódu. V Visual Basic je znak oddělovače dvojtečkou ( `:` ). Oddělovače použijte, pokud chcete zahrnout více příkazů na jeden řádek místo samostatných řádků. Tím ušetříte místo a zlepšíte čitelnost kódu. Následující příklad ukazuje tři příkazy oddělené dvojtečkami.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Další informace naleznete v tématu [How to: break and kombinovat příkazy v kódu](how-to-break-and-combine-statements-in-code.md).  
  
 Znak dvojtečky ( `:` ) slouží také k identifikaci popisku příkazu. Další informace naleznete v tématu [How to: Label Statements](how-to-label-statements.md).  
  
## <a name="concatenation"></a>Zřetězení  
 Použijte `&` operátor pro *zřetězení*nebo propojení řetězců dohromady. Nepleťte si ho s `+` operátorem, který přidá dohromady číselné hodnoty. Použijete-li `+` operátor k zřetězení při práci s číselnými hodnotami, můžete získat nesprávné výsledky. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Po provedení předchozího kódu se jedná o hodnotu `resultA` 21,01 a hodnota `resultB` je "10,0111".  
  
## <a name="member-access-operators"></a>Operátory přístupu členů  
 Chcete-li získat přístup ke členu typu, použijte operátor tečka ( `.` ) nebo vykřičník ( `!` ) mezi názvem typu a názvem člena.  
  
### <a name="dot--operator"></a>Tečka (.) Podnikatel  
 Použijte `.` operátor pro třídu, strukturu, rozhraní nebo výčet jako operátor přístupu členů. Členem může být pole, vlastnost, událost nebo metoda. Toto dokládá následující příklad.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Vykřičník (!) Podnikatel  
 Použijte `!` operátor pouze pro třídu nebo rozhraní jako operátor přístupu ke slovníku. Třída nebo rozhraní musí mít výchozí vlastnost, která přijímá jeden `String` argument. Identifikátor hned za `!` operátorem se bude hodnotou argumentu předanou výchozí vlastnosti jako řetězec. Následující příklad ukazuje to.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Tři výstupní řádky `MsgBox` všech zobrazuje hodnotu `32856` . První řádek používá tradiční přístup k vlastnosti `index` , druhá využívá fakt, který `index` je výchozí vlastností třídy `hasDefault` , a třetí používá slovník přístup ke třídě.  
  
 Všimněte si, že druhý operand `!` operátoru musí být platný identifikátor Visual Basic, který není uzavřen v uvozovkách ( `" "` ). Jinými slovy, nelze použít řetězcový literál nebo řetězcovou proměnnou. Následující změna na poslední řádek `MsgBox` volání vygeneruje chybu `"X"` , protože je uzavřený řetězcový literál.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Odkazy na výchozí kolekce musí být explicitní. Konkrétně nemůžete použít `!` operátor pro proměnnou s pozdní vazbou.  
  
 `!`Znak je také použit jako `Single` znak typu.  
  
## <a name="see-also"></a>Viz také

- [Struktura programu a konvence kódu](program-structure-and-code-conventions.md)
- [Znaky typu](../language-features/data-types/type-characters.md)
