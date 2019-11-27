---
title: Převody mezi řetězci a ostatními typy
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ac2e8ce912080c284d8ba0228830dd6b3ddf5f6e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350140"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Převody mezi řetězci a ostatními typy (Visual Basic)
Číselnou, `Boolean`nebo hodnotu data a času můžete převést na `String`. Můžete také převést v opačném směru – od řetězcové hodnoty na číslo, `Boolean`nebo `Date` – za předpokladu, že obsah řetězce může být interpretován jako platná hodnota cílového datového typu. Pokud se nedaří, dojde k chybě za běhu.  
  
 Převody všech těchto přiřazení v obou směrech mají zúžené převody. Měli byste použít klíčová slova konverze typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`a `CType`). Funkce <xref:Microsoft.VisualBasic.Strings.Format%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A> poskytují další kontrolu nad převody mezi řetězci a čísly.  
  
 Pokud jste definovali třídu nebo strukturu, můžete definovat operátory převodu typů mezi `String` a typem vaší třídy nebo struktury. Další informace naleznete v tématu [How to: define a Conversion operátor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Převod čísel na řetězce  
 Můžete použít funkci `Format` pro převod čísla na formátovaný řetězec, který může obsahovat nejen příslušné číslice, ale také formátování symbolů, jako je například symbol měny (například `$`), oddělovače tisíců nebo *symboly seskupování číslic* (například `,`) a oddělovač desetinných míst (například `.`). `Format` automaticky používá příslušné symboly podle nastavení **místních možností** zadaných v **Ovládacích panelech**systému Windows.  
  
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
