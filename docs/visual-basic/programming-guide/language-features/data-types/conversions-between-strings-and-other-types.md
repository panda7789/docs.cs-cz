---
title: Převody mezi řetězci a ostatními typy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 06dabbb5d5dfbfb545f01afb157fd532ca0551df
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197333"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Převody mezi řetězci a ostatními typy (Visual Basic)
Číselnou, `Boolean` nebo hodnotu data a času můžete převést na `String`. Můžete také převést v opačném směru – od řetězcové hodnoty na číslo, `Boolean` nebo `Date` – za předpokladu, že obsah řetězce může být interpretován jako platná hodnota cílového datového typu. Pokud se nedaří, dojde k chybě za běhu.  
  
 Převody všech těchto přiřazení v obou směrech mají zúžené převody. Měli byste použít klíčová slova konverze typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, 0, 1, 2 , 3 a 4). Funkce <xref:Microsoft.VisualBasic.Strings.Format%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A> poskytují další kontrolu nad převody mezi řetězci a čísly.  
  
 Pokud jste definovali třídu nebo strukturu, můžete definovat operátory převodu typů mezi `String` a typem vaší třídy nebo struktury. Další informace naleznete v tématu [How to: define a Conversion operátor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Převod čísel na řetězce  
 Pomocí funkce `Format` můžete převést číslo na formátovaný řetězec, který může obsahovat nejen příslušné číslice, ale také formátování symbolů, jako je například symbol měny (například `$`), oddělovače tisíců nebo *symboly seskupování číslic* (například @no __t_3) a oddělovač desetinných míst (například `.`). `Format` automaticky používá příslušné symboly podle nastavení **místních možností** zadaných v **Ovládacích panelech**systému Windows.  
  
 Všimněte si, že operátor zřetězení (`&`) může převést číslo na řetězec implicitně, jak ukazuje následující příklad.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Konverze řetězců na čísla  
 Pomocí funkce `Val` lze explicitně převést číslice v řetězci na číslo. `Val` přečte řetězec, dokud nenalezne znak, který je jiný než číslice, mezera, tabulátor, řádek nebo tečka. Sekvence "& O" a "& H" mění základ číselné soustavy a ukončí kontrolu. Dokud přestane číst, `Val` převede všechny příslušné znaky na číselnou hodnotu. Například následující příkaz vrátí hodnotu `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Když Visual Basic převede řetězec na číselnou hodnotu, použije nastavení **místní možnosti** zadané v **Ovládacích panelech** systému Windows k interpretaci oddělovače tisíců, oddělovače desetinných míst a symbolu měny. To znamená, že převod může být úspěšný při jednom nastavení, ale ne na jiném. Například `"$14.20"` je přijatelné v národním prostředí anglické (USA), ale ne v jakémkoli francouzském národním prostředí.  
  
## <a name="see-also"></a>Viz také:

- [Převody typu v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Postupy: převod objektu na jiný typ v Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Vývoj globálních a lokalizovaných aplikací](/visualstudio/ide/globalizing-and-localizing-applications)
