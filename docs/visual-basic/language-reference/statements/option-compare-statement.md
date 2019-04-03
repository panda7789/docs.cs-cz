---
title: Option Compare – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: b092d54e6cf4d8a96a35e6b1cc818fad8f26e3ae
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834072"
---
# <a name="option-compare-statement"></a>Option Compare – příkaz
Deklaruje výchozí metodu porovnání pro použití při porovnávání dat řetězců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`Binary`|Volitelné. Výsledkem porovnání řetězců na základě pořadí řazení, odvozený z vnitřní binární reprezentace znaků.<br /><br /> Tento typ porovnání je užitečný zejména v případě, že jsou řetězce mohou obsahovat znaky, které nemají být interpretován jako text. V takovém případě nechcete na posunu omezení porovnání s abecedním ekvivalence, jako je nerozlišování velikosti písmen.|  
|`Text`|Volitelné. Výsledky v závislosti na pořadí řazení nerozlišujícího velikost písmen textu určuje podle národního prostředí systému porovnávání řetězců.<br /><br /> Tento typ porovnání je užitečné, pokud vaše řetězce obsahují všechny textové znaky, a vy chcete jejich porovnání s ohledem na abecední ekvivalence účtu, jako je nerozlišování velikosti písmen a úzce související písmena. Například můžete chtít zvážit `A` a `a` musí rovnat, a `Ä` a `ä` před `B` a `b`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud použijete, `Option Compare` příkazu musí být uvedena v soubor předtím, než všechny ostatní příkazy zdrojového kódu.  
  
 `Option Compare` Příkaz určuje metodu porovnání řetězce (`Binary` nebo `Text`).  Výchozí metoda porovnání textu je `Binary`.  
  
 A `Binary` porovnání porovnává každý znak v každém řetězci číselnou hodnotu Unicode. A `Text` porovnání porovnává každý znak Unicode podle jeho lexikální význam v aktuální jazykové verze.  
  
 V Microsoft Windows pořadí řazení se určuje podle kódové stránky. Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).  
  
 V následujícím příkladu, znaků v znakové stránce (ANSI 1252) Angličtina/Evropské řazená pomocí `Option Compare Binary`, který vytváří typické binární řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Pokud řazená stejné znaky na stejné stránce kód pomocí `Option Compare Text`, je vytvořen textové řazení.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Když Option Compare – příkaz není k dispozici  
 Pokud zdrojový kód neobsahuje `Option Compare` příkazu **Option Compare** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud používáte kompilátoru příkazového řádku, nastavení určená [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru je používá.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Nastavení Option Compare v integrovaném vývojovém prostředí  
  
1.  V **Průzkumníka řešení**, vyberte projekt. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **kompilaci** kartu.  
  
3.  Nastavte hodnotu **Option Compare** pole.  
  
 Při vytváření projektu, **Option Compare** nastavení **kompilaci** karty nastavená na **Option Compare** nastavení **možnosti** Dialogové okno. Chcete-li změnit toto nastavení, na **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je **binární**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Nastavení Option Compare na příkazovém řádku  
  
-   Zahrnout [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) – možnost kompilátoru v **Vbc –** příkazu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Option Compare` příkaz nastavit jako výchozí metodu porovnání řetězce binární porovnání. Chcete-li tento kód použít, Odkomentujte `Option Compare Binary` příkaz a umístěte ho na začátku zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Option Compare` příkaz pro nastavení pořadí řazení nerozlišujícího velikost písmen textu jako výchozí metodu porovnání řetězce. Chcete-li tento kód použít, Odkomentujte `Option Compare Text` příkaz a umístěte ho na začátku zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)
- [Řetězcové funkce](../../../visual-basic/language-reference/functions/string-functions.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
