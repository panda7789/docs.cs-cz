---
title: Char – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796978"
---
# <a name="char-data-type-visual-basic"></a>Char – datový typ (Visual Basic)
Body bez znaménka 16bitový kódů (2bajtových) obsahuje v rozmezí od 0 do 65535. Každý *kódu bodu*, nebo kód znaku, představuje jeden znak Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Char` datového typu, když budete chtít obsahovat pouze jeden znak a není nutné režii `String`. V některých případech můžete použít `Char()`, pole `Char` prvků pro uložení více znaků.  
  
 Výchozí hodnota `Char` je znak s bodem kódu 0.  
  
## <a name="unicode-characters"></a>Znaky kódování Unicode  
 První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly na standardní klávesnici USA. Tyto první body 128 kódu jsou stejné jako definuje znakové sady ASCII. Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, symboly měny a podíly. Unicode používá pro širokou škálu symboly, včetně po celém světě textové znaky, diakritická znaménka a symboly technické a matematické zbývající body kódu (256 – 65535).  
  
 Můžete použít metody, jako je <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na `Char` proměnnou k určení jeho klasifikace kódování Unicode.  
  
## <a name="type-conversions"></a>Převody typu  
 Visual Basic nelze převést přímo mezi `Char` a číselné typy. Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkce pro převod `Char` hodnota, která se `Integer` , který představuje jeho bod kódu. Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkce pro převod `Integer` hodnota, která se `Char` , který má tento bod kódu.  
  
 Pokud kontrola typu ([Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)) je, – znak typu literálu musí připojit k literálu jedním znakem pro identifikaci jako `Char` datového typu. Toto dokládá následující příklad.  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>Tipy k programování  
  
- **Záporná čísla.** `Char` je typ bez znaménka a nemůže představovat záporné hodnoty. V každém případě byste neměli používat `Char` pro uložení číselné hodnoty.  
  
- **Spolupráce aspekty.** Pokud používáte rozhraní s komponentami, které nejsou napsané pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy znaků mají odlišnou datovou šířku (8 bitů) v jiných prostředích. Pokud takové součásti předáváte 8bitové argument, deklarujte ho jako `Byte` místo `Char` v váš nový kód jazyka Visual Basic.  
  
- **Rozšíření.** `Char` Datový typ rozšiřuje na `String`. To znamená, že můžete převést `Char` k `String` a nebude narazíte <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
- **Znaky typu.** Přidávání znak typu literálu `C` jeden znak řetězec literálu se z něj stane `Char` datového typu. `Char` nemá žádné – znak typu identifikátoru.  
  
- **Typ architektury.** Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktury.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Postupy: Volání funkce Windows, která přebírá typy bez znaménka](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
