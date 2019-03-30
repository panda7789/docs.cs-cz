---
title: Option Infer – příkaz (Visual Basic)
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
ms.openlocfilehash: 43ac5bc9e32892541ed2f9b0410b6e0ef10558a6
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654325"
---
# <a name="option-infer-statement"></a>Option Infer – příkaz
Umožňuje použití odvození místního typu v deklarujících proměnných.  
  
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
 Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru, než jakýkoli jiný zdrojový kód. Je-li nastavena hodnota pro `Option Infer` v souboru konflikty s hodnotou nastavenou v integrovaném vývojovém prostředí nebo na příkazovém řádku, hodnota v souboru má prioritu.  
  
 Pokud nastavíte `Option Infer` k `On`, bez explicitní uvedení datový typ je možné deklarovat lokální proměnné. Kompilátor odvodí datový typ proměnné z typu výrazu jeho inicializaci.  
  
 Na následujícím obrázku `Option Infer` zapnutý. Proměnné v deklaraci `Dim someVar = 2` je deklarován jako celé číslo odvození typu proměnné.

 Následující snímek obrazovky ukazuje technologie IntelliSense, když Option Infer na: 
  
 ![Snímek obrazovky s IntelliSense zobrazení Option Infer je na.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Na následujícím obrázku `Option Infer` je vypnutý. Proměnné v deklaraci `Dim someVar = 2` je deklarován jako `Object` podle odvození typu proměnné. V tomto příkladu **Option Strict** nastavená na **vypnout** na [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 Následující snímek obrazovky ukazuje technologie IntelliSense, když Option Infer je vypnuté:
 
 ![Snímek obrazovky zobrazení technologie IntelliSense při Option Infer je vypnuté.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  Pokud je proměnná deklarována jako `Object`, run-time typu můžete změnit, zatímco program běží. Visual Basic provádí operace volat *zabalení* a *rozbalení* k převodu mezi `Object` a typ hodnoty, takže provádění pomalejší. Informace o zabalení a rozbalení, najdete v článku [specifikace jazyka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).
  
 Odvození typu proměnné se vztahuje na úrovni postup a doporučení se netýká mimo proceduru v třída, struktura, modul nebo rozhraní.  
  
 Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Když Option Infer – příkaz není k dispozici  
 Pokud zdrojový kód neobsahuje `Option Infer` příkazu **Option Infer** nastavení [stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) se používá. Pokud se používá kompilátor příkazového řádku, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru je používá.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Nastavení Option Infer v integrovaném vývojovém prostředí  
  
1.  V **Průzkumníka řešení**, vyberte projekt. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
2.  Klikněte na tlačítko **kompilaci** kartu.  
  
3.  Nastavte hodnotu **Option infer** pole.  
  
 Když vytvoříte nový projekt **Option Infer** nastavení na **kompilaci** karty nastavená na **Option Infer** nastavení **VB výchozí** Dialogové okno. Pro přístup **VB výchozí** dialogovém okně **nástroje** nabídky, klikněte na tlačítko **možnosti**. V **možnosti** dialogového okna rozbalte **projekty a řešení**a potom klikněte na tlačítko **VB výchozí**. Počáteční výchozí nastavení v **výchozí hodnoty pro VB** je `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Chcete-li nastavit možnost Infer na příkazovém řádku  
  
-   Zahrnout [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) – možnost kompilátoru v **Vbc –** příkazu.  
  
## <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty  
 Následující tabulka popisuje výsledky různých kombinací určující typ dat a obsahuje inicializační proceduru `Dim` příkazu.  
  
|Zadaný datový typ?|Inicializátor zadaný?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí), je proměnná nastavena `Nothing`.<br /><br /> Pokud `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ne|Ano|`Dim qty = 5`|Pokud `Option Infer` je zapnuto (výchozí), zadejte proměnné přijímá data z inicializátoru. Zobrazit [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` je vypnuté, nabývá datový typ `Object`.<br /><br /> Pokud `Option Infer` je vypnuté a `Option Strict` zapnutý, dojde k chybě kompilace.|  
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro typ dat. Další informace najdete v tématu [příkazu Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátor není lze převést na zadaný datový typ, dojde k chybě kompilace.|  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak `Option Infer` příkaz povolí odvození místního typu.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že run-time typu se může lišit při proměnné se identifikuje jako `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Příkaz Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
