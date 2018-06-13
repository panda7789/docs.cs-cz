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
ms.openlocfilehash: 894638bbe50dad2cae1f74a2f7b7fe006f029d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592116"
---
# <a name="string-data-type-visual-basic"></a>String – datový typ (Visual Basic)
Obsahuje pořadí, bodů nepodepsaný kód (2bajtová) 16bitové rozsahu v rozmezí 0 až 65535. Každý *code bodu*, nebo kód znaku, představuje jeden znak Unicode. Řetězec může obsahovat od 0 do přibližně dvě miliardy (2 ^ 31) znaky znakové sady Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Použití `String` datový typ pro uložení více znaky bez režie na správu pole těchto `Char()`, pole `Char` elementy.  
  
 Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null). Všimněte si, že to není stejný jako prázdný řetězec (hodnota `""`).  
  
## <a name="unicode-characters"></a>Znaky kódování Unicode  
 První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly standardní klávesnicích. Tyto první 128 kód body jsou stejné jako definuje znaková sada ASCII. Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, tyto symboly a zlomků. Unicode používá zbývající body kódu (256 65 535) pro celou řadu symboly. To zahrnuje po celém světě textové znaky, znaky s diakritikou a matematické a technické symboly.  
  
 Můžete například použít metody <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivé znak v `String` proměnné můžete zjistit klasifikaci kódování Unicode.  
  
## <a name="format-requirements"></a>Požadavky na formát  
 Je nutné uzavřít `String` literálu do uvozovek (`" "`). Pokud jako jeden z znaků v řetězci musí zahrnovat uvozovky, můžete použít dva souvislý uvozovky (`""`). Toto dokládá následující příklad.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Upozorňujeme, že jsou souvislý uvozovky, které představují uvozovky v řetězci nezávislé na uvozovky, které začínají a končí `String` literálu.  
  
## <a name="string-manipulations"></a>Manipulace s řetězci  
 Po přiřazení řetězec tak, aby `String` proměnné, je tento řetězec *neměnné*, což znamená, že nelze změnit, jeho délka nebo obsah. Když upravíte řetězec žádným způsobem, Visual Basic vytvoří nový řetězec a opustí předchozí. `String` Proměnná se pak odkazuje na nový řetězec.  
  
 Můžete upravit obsah `String` proměnné pomocí celou řadu funkcí řetězec. Následující příklad ukazuje <xref:Microsoft.VisualBasic.Strings.Left%2A> – funkce  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Řetězec vytvořený jinou součástí může být doplněno počáteční nebo koncové mezery. Pokud se zobrazí tyto řetězce, můžete použít <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, a <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkce odebrat tyto prostory.  
  
 Další informace o manipulace s řetězci najdete v tématu [řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Tipy k programování  
  
-   **Záporná čísla.** Mějte na paměti, že znaky držené `String` nejsou podepsané a nemůže představují záporné hodnoty. V každém případě byste neměli používat `String` pro uložení číselné hodnoty.  
  
-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že řetězec znaků mají odlišné datové šířka (8 bitů) v jiných prostředích. Argument řetězce znaků 8bitové předáte pro tyto součásti, deklarujte ji jako `Byte()`, pole `Byte` elementy, místo `String` v váš nový kód jazyka Visual Basic.  
  
-   **Znaky typu.** Připojování znak typu identifikátoru `$` na všechny identifikátor vynutí ho k `String` datového typu. `String` nemá žádné – znak typu literálu. Ale kompilátor zpracovává literály uzavřena v uvozovkách (`" "`) jako `String`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.String?displayProperty=nameWithType> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.String?displayProperty=nameWithType>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
