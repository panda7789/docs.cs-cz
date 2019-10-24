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
ms.openlocfilehash: efd033e6c12637b8dc12fb886f46a267e677aa42
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775505"
---
# <a name="option-compare-statement"></a>Option Compare – příkaz
Deklaruje výchozí metodu porovnání, která se má použít při porovnávání řetězcových dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`Binary`|Volitelné. Výsledkem porovnání řetězců na základě pořadí řazení odvozeného z interních binárních reprezentace znaků.<br /><br /> Tento typ porovnání je užitečný hlavně v případě, že řetězce můžou obsahovat znaky, které nemusíte interpretovat jako text. V takovém případě nebudete chtít porovnání posunu s abecedními ekvivalenty, jako je například nerozlišování velkých a malých písmen.|  
|`Text`|Volitelné. Výsledkem porovnání řetězců na základě pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému.<br /><br /> Tento typ porovnání je užitečný v případě, že řetězce obsahují všechny textové znaky a chcete je porovnat s ohledem na abecední ekvivalenty, jako je například nerozlišování velkých a malých písmen a úzce související písmena. Například můžete chtít zvážit `A` a `a`, které mají být stejné, a `Ä` a `ä` k předcházet `B` a `b`.|  
  
## <a name="remarks"></a>Poznámky  
 Při použití musí být příkaz `Option Compare` uveden v souboru před jakýmkoli jiným příkazy zdrojového kódu.  
  
 Příkaz `Option Compare` určuje metodu porovnání řetězců (`Binary` nebo `Text`).  Výchozí metoda porovnání textu je `Binary`.  
  
 Porovnání `Binary` porovnává číselnou hodnotu Unicode každého znaku v každém řetězci. Porovnání `Text` porovnává každý znak Unicode na základě jeho lexikálního významu v aktuální jazykové verzi.  
  
 V systému Microsoft Windows je pořadí řazení určeno znakovou stránkou. Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).  
  
 V následujícím příkladu jsou znaky na znakové stránce angličtina/Evropa (ANSI 1252) řazeny pomocí `Option Compare Binary`, což vytváří typické binární pořadí řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Když jsou stejné znaky na stejné znakové stránce seřazené pomocí `Option Compare Text`, vytvoří se následující textové pořadí řazení.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Pokud není k dispozici příkaz Option Compare  
 Pokud zdrojový kód neobsahuje příkaz `Option Compare`, je použita **možnost porovnat** nastavení na [stránce kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Použijete-li kompilátor příkazového řádku, je použito nastavení určené možností kompilátoru [-OptionCompare –](../../../visual-basic/reference/command-line-compiler/optioncompare.md) .  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Nastavení možnosti Compare v integrovaném vývojovém prostředí  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **kompilovat** .  
  
3. Nastavte hodnotu v poli **Porovnat možnost** .  
  
 Při vytváření projektu je **možnost porovnat** nastavení na kartě **kompilovat** nastavena na **možnost porovnat** nastavení v dialogovém okně **Možnosti** . Chcete-li toto nastavení změnit, v nabídce **nástroje** klikněte na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení ve **výchozích hodnotách VB** je **binární**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Nastavení možnosti Compare v příkazovém řádku  
  
- Do příkazu **Vbc** zahrňte možnost kompilátoru [-OptionCompare –](../../../visual-basic/reference/command-line-compiler/optioncompare.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Option Compare` pro nastavení binárního porovnání jako výchozí metody porovnání řetězců. Chcete-li použít tento kód, odkomentujte příkaz `Option Compare Binary` a umístěte jej do horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Option Compare` pro nastavení pořadí řazení textu bez rozlišení velkých a malých písmen jako výchozí metodu porovnání řetězců. Chcete-li použít tento kód, odkomentujte příkaz `Option Compare Text` a umístěte jej do horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátor Like](../../../visual-basic/language-reference/operators/like-operator.md)
- [Funkce řetězce](../../../visual-basic/language-reference/functions/string-functions.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
