---
title: Option Infer – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: c7628e5c4c0cda527a4c3b1a211c45760640fc63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="option-infer-statement"></a>Option Infer – příkaz
Umožňuje použití odvození místního typu v deklarování proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`On`|Volitelné. Umožňuje odvození místního typu.|  
|`Off`|Volitelné. Zakáže odvození místního typu.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, před spuštěním zdrojového kódu. Pokud je hodnota nastavená pro `Option Infer` souboru konflikty s hodnotu nastavenou v prostředí IDE nebo na příkazovém řádku, v souboru hodnota má vyšší prioritu.  
  
 Když nastavíte `Option Infer` k `On`, místní proměnné můžou deklarovat bez explicitně s informacemi o tom datový typ. Kompilátor odvodí datový typ proměnné z typu jejího výrazu inicializace.  
  
 Na následujícím obrázku `Option Infer` je zapnutý. Proměnné v deklaraci `Dim someVar = 2` je deklarovaná odvození typu jako celé číslo.  
  
 ![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")  
Option Infer – je na IntelliSense  
  
 Na následujícím obrázku `Option Infer` je vypnutý. Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu. V tomto příkladu **možnost striktní** nastavení je **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 ![Zobrazení technologie IntelliSense deklarace. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")  
IntelliSense při Option Infer – vypnuté  
  
> [!NOTE]
>  Když je proměnná deklarován jako `Object`, při spuštění programu, můžete změnit typ spuštění. Visual Basic provádí operace názvem *zabalení* a *rozbalení* pro převod mezi `Object` a typ hodnoty, které umožňuje provádění pomalejší. Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](../../../visual-basic/reference/language-specification/index.md).
  
 Odvození typu se vztahuje na úrovni procedury a doporučení se netýká mimo proceduru v třída, struktura, modulu nebo rozhraní.  
  
 Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Když Option Infer – příkaz není k dispozici  
 Pokud zdrojový kód neobsahuje `Option Infer` příkaz, **Option Infer –** nastavení na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud se používá kompilátoru příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru se používá.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Chcete-li nastavit Option Infer – v prostředí IDE  
  
1.  V **Průzkumníku**, vyberte projektu. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Nastavte hodnotu v **Option infer –** pole.  
  
 Při vytvoření nového projektu, **Option Infer –** nastavení na **zkompilovat** karta je nastaven na **Option Infer –** nastavení v **VB výchozí** Dialogové okno. Pro přístup k **VB výchozí** v dialogovém **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogové okno, rozbalte seznam **projekty a řešení**a potom klikněte na **VB výchozí**. Počáteční výchozí nastavení v **VB výchozí** je `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Chcete-li nastavit Option Infer – na příkazovém řádku  
  
-   Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkaz.  
  
## <a name="default-data-types-and-values"></a>Typy a hodnoty výchozí Data  
 Následující tabulka popisuje výsledky datový typ a inicializátoru v různých kombinacích `Dim` příkaz.  
  
|Datový typ zadaný?|Zadaný inicializační?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí), proměnná je nastavená na `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ne|Ano|`Dim qty = 5`|Pokud `Option Infer` je na (výchozí), typ inicializátoru proměnné přijímá data. V tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` je vypnutý, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ano|Ne|`Dim qty As Integer`|Výchozí hodnota pro typ dat je inicializováno proměnnou. Další informace najdete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru není převést na zadaný datový typ, dojde k chybě kompilace.|  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že běhového typu se může lišit při proměnné je označený `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
