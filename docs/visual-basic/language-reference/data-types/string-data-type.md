---
title: Datový typ String
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: c2c6f9632646c432abb7b6da8887253e526cc994
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343908"
---
# <a name="string-data-type-visual-basic"></a>String – datový typ (Visual Basic)

Obsahuje sekvence nepodepsaných 16bitových (2-bajtových) bodů kódu, které jsou v rozsahu od 0 do 65535. Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode. Řetězec může obsahovat 0 až přibližně 2 000 000 000 (2 ^ 31) znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  

 Použijte datový typ `String` k uložení více znaků bez režie správy pole `Char()`, pole prvků `Char`.  
  
 Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null). Všimněte si, že se neshoduje s prázdným řetězcem (hodnota `""`).  
  
## <a name="unicode-characters"></a>Znaky Unicode  

 Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici. Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII. Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky. Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů. To zahrnuje celosvětově textové znaky, diakritická znaménka a matematické a technické symboly.  
  
 Můžete použít metody jako <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivém znaku v proměnné `String` k určení klasifikace Unicode.  
  
## <a name="format-requirements"></a>Požadavky na formát  

 Literál `String` musíte uzavřít do uvozovek (`" "`). Pokud je nutné zadat uvozovky jako jeden ze znaků v řetězci, použijete dva souvislé uvozovky (`""`). Toto dokládá následující příklad.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Všimněte si, že souvislé uvozovky, které představují uvozovky v řetězci, jsou nezávislé na uvozovkách, které začínají a končí literál `String`.  
  
## <a name="string-manipulations"></a>Manipulace s řetězci  

 Po přiřazení řetězce k proměnné `String` je tento řetězec *neměnný*, což znamená, že nemůžete změnit jeho délku nebo obsah. Při změně řetězce jakýmkoli způsobem Visual Basic vytvoří nový řetězec a opustí předchozí. Proměnná `String` potom odkazuje na nový řetězec.  
  
 Můžete manipulovat s obsahem `String` proměnné pomocí nejrůznějších řetězcových funkcí. Následující příklad ilustruje funkci <xref:Microsoft.VisualBasic.Strings.Left%2A>.  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Řetězec vytvořený jinou komponentou může být doplněn mezerami na začátku nebo na konci. Pokud tento řetězec obdržíte, můžete k odebrání těchto prostorů použít funkce <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>a <xref:Microsoft.VisualBasic.Strings.RTrim%2A>.  
  
 Další informace o manipulaci s řetězci naleznete v tématu [strings](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Záporná čísla.** Mějte na paměti, že znaky držené `String` jsou bez znaménka a nemohou představovat záporné hodnoty. V žádném případě byste neměli používat `String` k ukládání číselných hodnot.  
  
- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že řetězcové znaky mají v jiných prostředích jinou šířku dat (8 bitů). Pokud předáte řetězcové argumenty 8bitových znaků této součásti, deklarujte ji jako `Byte()`, pole `Byte` prvků místo `String` v novém kódu Visual Basic.  
  
- **Znaky typu.** Připojení znaku typu identifikátoru `$` k jakémukoli identifikátoru vynutí `String` datový typ. `String` nemá žádný znak typu literálu. Nicméně Kompilátor považuje literály uzavřené v uvozovkách (`" "`) jako `String`.  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je třída <xref:System.String?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.String?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
