---
title: String – datový typ (Visual Basic)
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
ms.openlocfilehash: 54f7dcd7de28e8aaa5376bb4ddd67fd53518511e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661551"
---
# <a name="string-data-type-visual-basic"></a>String – datový typ (Visual Basic)
Obsahuje pořadí bodů kódu (2bajtových) bez znaménka 16bitové tohoto rozsahu v rozmezí 0 až 65535. Každý *kódu bodu*, nebo kód znaku, představuje jeden znak Unicode. Řetězec se může skládat z 0 až přibližně dvě miliardy (2 ^ 31) znaků Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Použití `String` datový typ pro uložení více znaků bez režie na správu pole těchto `Char()`, pole `Char` elementy.  
  
 Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null). Všimněte si, že to není stejné jako prázdný řetězec (hodnota `""`).  
  
## <a name="unicode-characters"></a>Znaky kódování Unicode  
 První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly na standardní klávesnici USA. Tyto první body 128 kódu jsou stejné jako definuje znakové sady ASCII. Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, symboly měny a podíly. Unicode používá pro širokou škálu symboly zbývající body kódu (256 – 65535). To zahrnuje po celém světě textové znaky, znaky s diakritikou a technické a matematické symboly.  
  
 Můžete například použít metody <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivý znak ve `String` proměnnou k určení jeho klasifikace kódování Unicode.  
  
## <a name="format-requirements"></a>Požadavky na formát  
 Je nutné uzavřít `String` literál v uvozovkách (`" "`). Pokud jako jeden ze znaků v řetězci musí obsahovat znak uvozovek, je použít dva souvislých uvozovky (`""`). Toto dokládá následující příklad.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Mějte na paměti, že jsou souvislé uvozovky, které představují uvozovka v řetězci nezávislé na uvozovky, které začínají i končí `String` literálu.  
  
## <a name="string-manipulations"></a>Manipulace s řetězci  
 Po přiřazení řetězec `String` proměnné, je tento řetězec *neměnné*, což znamená, že nelze změnit jeho délka nebo obsah. Při změně řetězec žádným způsobem jazyka Visual Basic vytvoří nový řetězec a opustí předchozí. `String` Proměnná se pak odkazuje na nový řetězec.  
  
 Můžete manipulovat s obsahem `String` proměnné pomocí celé řady funkcí řetězec. Následující příklad ukazuje, <xref:Microsoft.VisualBasic.Strings.Left%2A> – funkce  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Řetězec vytvořené jinou komponentou může být, aby bylo vytvořeno úvodní a koncové mezery. Pokud obdržíte takový řetězec, můžete použít <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, a <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkce odebrat tyto mezery.  
  
 Další informace o manipulace s řetězci, naleznete v tématu [řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Záporná čísla.** Mějte na paměti, že znaky drží `String` jsou bez znaménka a nemůže představovat záporné hodnoty. V každém případě byste neměli používat `String` pro uložení číselné hodnoty.  
  
-   **Spolupráce aspekty.** Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že řetězec znaků mít odlišnou datovou šířku (8 bitů) v jiných prostředích. Pokud takové součásti předáváte argument řetězec znaků 8 bitů, deklarujte ho jako `Byte()`, pole `Byte` prvků, místo `String` v váš nový kód jazyka Visual Basic.  
  
-   **Znaky typu.** Přidávání znak typu identifikátoru `$` k libovolnému identifikátoru se z něj stane `String` datového typu. `String` nemá žádné – znak typu literálu. Ale kompilátor zpracovává literály uzavřena v uvozovkách (`" "`) jako `String`.  
  
-   **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.String?displayProperty=nameWithType> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/index.md)  
 [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
