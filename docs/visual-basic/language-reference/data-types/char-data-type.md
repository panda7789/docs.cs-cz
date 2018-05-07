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
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="char-data-type-visual-basic"></a>Char – datový typ (Visual Basic)
Blokování nepodepsaného kódu (2bajtová) 16bitové body v rozmezí od 0 do 65535. Každý *code bodu*, nebo kód znaku, představuje jeden znak Unicode.  
  
## <a name="remarks"></a>Poznámky  
 Použití `Char` datový typ, když potřebujete obsahovat jenom jeden znak a není nutné nároky na `String`. V některých případech můžete použít `Char()`, pole `Char` elementy pro uložení více znaků.  
  
 Výchozí hodnota `Char` je znak s bodem kód 0.  
  
## <a name="unicode-characters"></a>Znaky kódování Unicode  
 První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly standardní klávesnicích. Tyto první 128 kód body jsou stejné jako definuje znaková sada ASCII. Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, tyto symboly a zlomků. Unicode používá zbývající body kódu (256 65 535) pro širokou škálu symboly, včetně po celém světě textové znaky, znaky s diakritikou a matematické a technické symboly.  
  
 Můžete použít metody, třeba <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na `Char` proměnné můžete zjistit klasifikaci kódování Unicode.  
  
## <a name="type-conversions"></a>Převody typu  
 Visual Basic nepřevede přímo mezi `Char` a číselnými typy. Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkce pro převod `Char` hodnotu `Integer` představující jeho bod kódu. Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkce pro převod `Integer` hodnotu `Char` obsahujícím bod tohoto kódu.  
  
 Pokud kontrola typu přepínač ([Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)) je na znak typu literálu musí připojit k délce jednoho znaku řetězcový literál pro identifikaci jako `Char` datového typu. Toto dokládá následující příklad.  
  
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
  
-   **Záporná čísla.** `Char` je typu bez znaménka a nemůže představují zápornou hodnotu. V každém případě byste neměli používat `Char` pro uložení číselné hodnoty.  
  
-   **Spolupráce aspekty.** Pokud rozhraní s komponentami nezapíše pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy znaků mají různé datové šířka (8 bitů) v jiných prostředích. Pokud předáte 8bitové argument pro tyto součásti, deklarujte ji jako `Byte` místo `Char` v váš nový kód jazyka Visual Basic.  
  
-   **Rozšíření.** `Char` Datový typ rozšiřuje na `String`. To znamená, že můžete převést `Char` k `String` a nebude narazíte <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znak typu literálu `C` na řetězec délce jednoho znaku literál vynutí, aby `Char` datového typu. `Char` nemá žádné – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
