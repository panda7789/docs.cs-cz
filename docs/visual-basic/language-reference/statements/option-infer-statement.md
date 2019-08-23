---
title: Option odvod – příkaz (Visual Basic)
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
ms.openlocfilehash: e7f5fcc6d76f654f53eea6677962cb097e98b881
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912303"
---
# <a name="option-infer-statement"></a>Option Infer – příkaz
Umožňuje použití odvození místního typu v deklaraci proměnných.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`On`|Volitelný parametr. Povoluje odvození místního typu.|  
|`Off`|Volitelný parametr. Zakáže odvození místního typu.|  
  
## <a name="remarks"></a>Poznámky  
 Chcete- `Option Infer` li nastavit v souboru, `Option Infer On` zadejte `Option Infer Off` nebo v horní části souboru před jakýkoliv jiný zdrojový kód. Pokud je hodnota nastavená `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.  
  
 Když nastavíte `Option Infer` na `On`, můžete deklarovat místní proměnné bez explicitního oznámení datového typu. Kompilátor odvodí datový typ proměnné z typu jeho inicializačního výrazu.  
  
 Na následujícím obrázku `Option Infer` je zapnutý. Proměnná v deklaraci `Dim someVar = 2` je deklarována jako celé číslo podle odvození typu.

 Následující snímek obrazovky ukazuje IntelliSense, pokud je možnost odvozená: 
  
 ![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je zapnutá možnost odvodit.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Na následujícím obrázku `Option Infer` je vypnutý. Proměnná v deklaraci `Dim someVar = 2` je deklarována `Object` jako odvození typu. V tomto příkladu je **možnost Option Strict** nastavená na hodnotu **vypnuto** na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 Následující snímek obrazovky ukazuje IntelliSense, pokud je volba odvoditelné:
 
 ![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je volba odvoditelné](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
> Pokud je proměnná deklarována jako `Object`, typ za běhu se může změnit během běhu programu. Visual Basic provádí operace označované jako zabalení a rozbalení pro `Object` převod mezi a hodnotovým typem, což činí provádění pomaleji. Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).
  
 Odvození typu se vztahuje na úroveň procedury a neplatí mimo proceduru ve třídě, struktuře, modulu nebo rozhraní.  
  
 Další informace naleznete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>Pokud není k dispozici příkaz k odvození možnosti  
 Pokud zdrojový kód `Option Infer` neobsahuje příkaz, je použita **možnost odvodit** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Pokud je použit kompilátor příkazového řádku, je použita možnost kompilátoru [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) .  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Nastavení volby odvoditelné v integrovaném vývojovém prostředí  
  
1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
2. Klikněte na kartu **kompilovat** .  
  
3. Nastavte hodnotu v poli odvoditelné **Možnosti** .  
  
 Při vytváření nového projektu je **možnost odvodit** nastavení na kartě **kompilovat** nastavena na **možnost odvodit** nastavení v dialogovém okně **výchozí hodnoty VB** . Chcete-li získat přístup k dialogovému oknu **výchozí hodnoty VB** , v nabídce **nástroje** klikněte na možnost **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Výchozí výchozí nastavení ve výchozím nastavení **jazyka VB** je `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Nastavení možnosti odvození v příkazovém řádku  
  
- Do příkazu **Vbc** zahrňte možnost kompilátoru [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) .  
  
## <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty  
 Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v `Dim` příkazu.  
  
|Byl zadán datový typ?|Byl určen inicializátor?|Příklad|Výsledek|  
|---|---|---|---|  
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí nastavení), proměnná je nastavena na `Nothing`.<br /><br /> Pokud `Option Strict` je, dojde k chybě při kompilaci.|  
|Ne|Ano|`Dim qty = 5`|Pokud `Option Infer` je zapnuto (výchozí), proměnná převezme datový typ inicializátoru. Viz [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnutý `Option Strict` a je vypnutý, proměnná `Object`vezme datový typ.<br /><br /> Pokud `Option Infer` je vypnutý `Option Strict` a je zapnutý, dojde k chybě při kompilaci.|  
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro datový typ. Další informace naleznete v tématu [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.|  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, že běhový typ se může lišit, když je proměnná identifikována jako `Object`.  
  
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
