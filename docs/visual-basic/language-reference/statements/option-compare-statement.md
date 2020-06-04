---
title: Option Compare – příkaz
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
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404379"
---
# <a name="option-compare-statement"></a>Option Compare – příkaz
Deklaruje výchozí metodu porovnání, která se má použít při porovnávání řetězcových dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`Binary`|Nepovinný parametr. Výsledkem porovnání řetězců na základě pořadí řazení odvozeného z interních binárních reprezentace znaků.<br /><br /> Tento typ porovnání je užitečný hlavně v případě, že řetězce můžou obsahovat znaky, které nemusíte interpretovat jako text. V takovém případě nebudete chtít porovnání posunu s abecedními ekvivalenty, jako je například nerozlišování velkých a malých písmen.|  
|`Text`|Nepovinný parametr. Výsledkem porovnání řetězců na základě pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému.<br /><br /> Tento typ porovnání je užitečný v případě, že řetězce obsahují všechny textové znaky a chcete je porovnat s ohledem na abecední ekvivalenty, jako je například nerozlišování velkých a malých písmen a úzce související písmena. Například můžete chtít vzít v úvahu, že chcete se rovnat a a `A` `a` použít `Ä` `ä` před `B` a `b` .|  
  
## <a name="remarks"></a>Poznámky  
 Je-li použit, `Option Compare` příkaz se musí objevit v souboru před jakýmkoli jiným příkazy zdrojového kódu.  
  
 `Option Compare`Příkaz určuje metodu porovnání řetězců ( `Binary` nebo `Text` ).  Výchozí metoda porovnání textu je `Binary` .  
  
 `Binary`Porovnání porovnává číselnou hodnotu Unicode každého znaku v každém řetězci. `Text`Porovnání porovnává každý znak Unicode na základě jeho lexikálního významu v aktuální jazykové verzi.  
  
 V systému Microsoft Windows je pořadí řazení určeno znakovou stránkou. Další informace najdete v tématu [znakové stránky](/cpp/c-runtime-library/code-pages).  
  
 V následujícím příkladu jsou znaky na znakové stránce angličtina/Evropa (ANSI 1252) řazeny pomocí příkazu `Option Compare Binary` , který vytváří typické binární pořadí řazení.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Pokud jsou stejné znaky na stejné znakové stránce seřazené pomocí `Option Compare Text` , je vytvořen následující text pořadí řazení.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>Pokud není k dispozici příkaz Option Compare  
 Pokud zdrojový kód neobsahuje `Option Compare` příkaz, je použita **možnost porovnat** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Použijete-li kompilátor příkazového řádku, je použito nastavení určené možností kompilátoru [-OptionCompare –](../../reference/command-line-compiler/optioncompare.md) .  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Nastavení možnosti Compare v integrovaném vývojovém prostředí  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **kompilovat** .  
  
3. Nastavte hodnotu v poli **Porovnat možnost** .  
  
 Při vytváření projektu je **možnost porovnat** nastavení na kartě **kompilovat** nastavena na **možnost porovnat** nastavení v dialogovém okně **Možnosti** . Chcete-li toto nastavení změnit, v nabídce **nástroje** klikněte na příkaz **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Počáteční výchozí nastavení ve **výchozích hodnotách VB** je **binární**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Nastavení možnosti Compare v příkazovém řádku  
  
- Do příkazu **Vbc** zahrňte možnost kompilátoru [-OptionCompare –](../../reference/command-line-compiler/optioncompare.md) .  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Compare` příkaz pro nastavení binárního porovnání jako výchozí metody porovnání řetězců. Chcete-li použít tento kód, odkomentujte `Option Compare Binary` příkaz a umístěte jej do horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Option Compare` příkaz k nastavení pořadí řazení textu bez rozlišování velkých a malých písmen jako výchozí metody porovnání řetězců. Chcete-li použít tento kód, odkomentujte `Option Compare Text` příkaz a umístěte jej do horní části zdrojového souboru.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [Operátory porovnání](../operators/comparison-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like – operátor](../operators/like-operator.md)
- [Řetězcové funkce](../functions/string-functions.md)
- [Option Explicit – příkaz](option-explicit-statement.md)
- [Option Strict – příkaz](option-strict-statement.md)
