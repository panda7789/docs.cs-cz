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
ms.openlocfilehash: 38acd9056f9517e6d8b62691cdeb1a2960bec800
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516571"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Převody mezi řetězci a ostatními typy (Visual Basic)
Lze převést číselnou, `Boolean`, nebo hodnotu data a času `String`. Můžete také převést v opačném směru – z řetězcové hodnoty na číselnou hodnotu, `Boolean`, nebo `Date` – zadaný obsah řetězce může být interpretován jako platná hodnota cílového datového typu. Pokud to není možné, dojde k chybě za běhu.  
  
 Převody pro všechna tato přiřazení v obou směrech jsou zužujících převodů. Měli byste použít klíčová slova převodu typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, a `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkce poskytují větší kontrolu nad převody mezi řetězci a čísla.  
  
 Pokud jste definovali třídy nebo struktury, můžete definovat operátory převodů typu mezi `String` a typ třídy nebo struktury. Další informace najdete v tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Převod čísla na řetězce  
 Můžete použít `Format` funkce pro převod čísla na formátovaný řetězec, který může obsahovat pouze odpovídající číslic, ale také formátování symboly, jako je symbolem měny (například `$`), tisíců oddělovače nebo *seskupení číslic symboly* (například `,`) a oddělovač desetinných míst (například `.`). `Format` automaticky použije příslušné symbolů podle **místní nastavení** nastavení uvedená v Windows **ovládací panely**.  
  
 Všimněte si, že zřetězení (`&`) – operátor lze implicitně převést na číslo na řetězec, jak ukazuje následující příklad.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Převod řetězců na čísla  
 Můžete použít `Val` funkce k explicitnímu převodu číslice v řetězci na číslo. `Val` načte řetězec, dokud nenarazí na znak jiný než číslice, místa, tabulátor, odřádkování nebo období. Sekvence "& O" a "& H" alter základ číselné soustavy a ukončit skenování. Dokud se zastaví čtení, `Val` převede všechny odpovídající znaky na číselnou hodnotu. Například následující příkaz vrátí hodnotu `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic převede řetězec na číselnou hodnotu, použije **místní nastavení** nastavení uvedená v Windows **ovládací panely** k interpretaci tisíců oddělovač, oddělovač desetinných míst, a symbol měny. To znamená, že převod může proběhnout úspěšně pod jednou, ale nejsou jiné nastavení. Například `"$14.20"` je přijatelné v národním prostředí Angličtina (Spojené státy), ale ne v jakékoli francouzské národní prostředí.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Představení mezinárodních aplikací založených na prostředí .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
