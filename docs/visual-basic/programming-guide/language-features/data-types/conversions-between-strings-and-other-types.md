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
ms.openlocfilehash: 40a28d664bc6ed3d094ccc7c342d6411fe88fd7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650566"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Převody mezi řetězci a ostatními typy (Visual Basic)
Můžete převést jednu číslici, `Boolean`, nebo hodnotu data a času `String`. Můžete také převést v opačném směru – z řetězcové hodnoty číselné literály, `Boolean`, nebo `Date` – zadaný řetězec obsah lze interpretovat jako platná hodnota cílový datový typ. Pokud to není možné, dojde k chybě spuštění.  
  
 Převody pro všechny tyto úlohy, v obou směrech jsou zužující převody. Měli byste použít klíčová slova převodu typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, a `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkce získáte další kontrolu nad převody mezi řetězci a čísla.  
  
 Pokud jste definovali třídu nebo strukturu, můžete definovat operátory převodu typu mezi `String` a typ třídu nebo strukturu. Další informace najdete v tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Převádění čísla na řetězce  
 Můžete použít `Format` funkce převodu čísla na řetězec formátovaný, která může zahrnovat nejen příslušné číslic, ale také formátování symboly, jako je currency přihlašovací (například `$`), tisíc oddělovačů nebo *seskupování číslic symboly* (například `,`) a oddělovač desetinných míst (například `.`). `Format` automaticky použije příslušné symboly podle požadavků **místní nastavení** nastavení zadané v systému Windows **ovládací panely**.  
  
 Všimněte si, že zřetězení (`&`) operátor můžete čísla na řetězec implicitně převést, jak ukazuje následující příklad.  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Převod řetězců na čísla  
 Můžete použít `Val` funkce explicitně převést číslic v řetězec na číslo. `Val` načte řetězec, dokud zjistí znak než číslice, místo, karta, nového řádku nebo období. Daná pořadí "& O" a "& H" alter základní číslo systému a ukončete kontrolu. Končí čtení, `Val` převede všechny znaky odpovídající číselná hodnota. Například následující příkaz vrátí hodnotu `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic převede řetězec na číselnou hodnotu, použije **místní nastavení** nastavení zadané v systému Windows **ovládací panely** interpretovat tisíců oddělovač, oddělovač desetinných míst a symbolu měny. To znamená, že převodu z může úspěšné pod jednou, ale není jiná nastavení. Například `"$14.20"` je přijatelné v národním prostředí Czech (Czech Republic), ale není v kterémkoli národním prostředí francouzštině.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Představení mezinárodních aplikací založených na prostředí .NET Framework](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
