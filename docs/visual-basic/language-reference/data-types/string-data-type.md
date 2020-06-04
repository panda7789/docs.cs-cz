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
ms.openlocfilehash: cd4b64c101ae56928e84a04649e49c17b6f4023c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415502"
---
# <a name="string-data-type-visual-basic"></a>String – datový typ (Visual Basic)

Obsahuje sekvence nepodepsaných 16bitových (2-bajtových) bodů kódu, které jsou v rozsahu od 0 do 65535. Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode. Řetězec může obsahovat 0 až přibližně 2 000 000 000 (2 ^ 31) znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  

 Použijte `String` datový typ pro uložení více znaků bez režie správy pole `Char()` , pole `Char` prvků.  
  
 Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null). Všimněte si, že se neshoduje s prázdným řetězcem (hodnota `""` ).  
  
## <a name="unicode-characters"></a>Znaky Unicode  

 Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici. Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII. Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky. Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů. To zahrnuje celosvětově textové znaky, diakritická znaménka a matematické a technické symboly.  
  
 Pomocí metod, jako je <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivém znaku v proměnné, můžete `String` určit svou klasifikaci Unicode.  
  
## <a name="format-requirements"></a>Požadavky na formát  

 Je nutné uzavřít `String` literál v uvozovkách ( `" "` ). Pokud je nutné uvozovky obsahovat jako jeden ze znaků v řetězci, použijete dvě souvislé uvozovky ( `""` ). Toto dokládá následující příklad.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Všimněte si, že souvislé uvozovky, které představují uvozovky v řetězci, jsou nezávislé na uvozovkách, které začínají a končí `String` literál.  
  
## <a name="string-manipulations"></a>Manipulace s řetězci  

 Po přiřazení řetězce k `String` proměnné je tento řetězec *neměnný*, což znamená, že nemůžete změnit jeho délku nebo obsah. Při změně řetězce jakýmkoli způsobem Visual Basic vytvoří nový řetězec a opustí předchozí. `String`Proměnná pak odkazuje na nový řetězec.  
  
 Můžete manipulovat s obsahem `String` proměnné pomocí nejrůznějších řetězcových funkcí. Následující příklad ilustruje <xref:Microsoft.VisualBasic.Strings.Left%2A> funkci  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Řetězec vytvořený jinou komponentou může být doplněn mezerami na začátku nebo na konci. Pokud tento řetězec obdržíte, můžete <xref:Microsoft.VisualBasic.Strings.Trim%2A> <xref:Microsoft.VisualBasic.Strings.LTrim%2A> <xref:Microsoft.VisualBasic.Strings.RTrim%2A> k odebrání těchto mezer použít funkce, a.  
  
 Další informace o manipulaci s řetězci naleznete v tématu [strings](../../programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Záporná čísla.** Pamatujte, že znaky uchovávané `String` jsou bez znaménka a nemohou představovat záporné hodnoty. V žádném případě byste neměli používat `String` k ukládání číselných hodnot.  
  
- **Problematika spolupráce.** Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že řetězcové znaky mají v jiných prostředích jinou šířku dat (8 bitů). Pokud předáte řetězcové argumenty 8bitových znaků této součásti, deklarujte ji jako `Byte()` , pole `Byte` prvků, nikoli `String` v novém kódu Visual Basic.  
  
- **Znaky typu.** Připojení znaku typu identifikátoru `$` k jakémukoli identifikátoru vynutí `String` datový typ. `String`nemá žádný znak typu literálu. Nicméně kompilátor zpracovává literály, které jsou uzavřeny v uvozovkách ( `" "` ) jako `String` .  
  
- **Typ rozhraní.** Odpovídající typ v .NET Framework je <xref:System.String?displayProperty=nameWithType> Třída.  
  
## <a name="see-also"></a>Viz také

- <xref:System.String?displayProperty=nameWithType>
- [Datové typy](index.md)
- [Char – datový typ](char-data-type.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Souhrn převodu](../keywords/conversion-summary.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
