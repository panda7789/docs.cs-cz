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
ms.openlocfilehash: 977e492c1c8ec5040c22169d91268c9c2241f6c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404353"
---
# <a name="option-infer-statement"></a>Option Infer – příkaz

Umožňuje použití odvození místního typu v deklaraci proměnných.

## <a name="syntax"></a>Syntaxe

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>Součásti

|Pojem|Definice|
|---|---|
|`On`|Nepovinný parametr. Povoluje odvození místního typu.|
|`Off`|Nepovinný parametr. Zakáže odvození místního typu.|

## <a name="remarks"></a>Poznámky

Chcete-li nastavit `Option Infer` v souboru, zadejte `Option Infer On` nebo `Option Infer Off` v horní části souboru před jakýkoliv jiný zdrojový kód. Pokud je hodnota nastavená `Option Infer` v souboru v konfliktu s hodnotou nastavenou v integrovaném vývojovém prostředí (IDE) nebo na příkazovém řádku, má hodnota v souboru přednost.

Když nastavíte `Option Infer` na `On` , můžete deklarovat místní proměnné bez explicitního oznámení datového typu. Kompilátor odvodí datový typ proměnné z typu jeho inicializačního výrazu.

Na následujícím obrázku `Option Infer` je zapnutý. Proměnná v deklaraci `Dim someVar = 2` je deklarována jako celé číslo podle odvození typu.

Následující snímek obrazovky ukazuje IntelliSense, pokud je možnost odvozená:

![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je zapnutá možnost odvodit.](./media/option-infer-statement/option-infer-as-integer-on.png)

Na následujícím obrázku je vypnutý `Option Infer` . Proměnná v deklaraci `Dim someVar = 2` je deklarována jako `Object` odvození typu. V tomto příkladu je **možnost Option Strict** nastavená na hodnotu **vypnuto** na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

Následující snímek obrazovky ukazuje IntelliSense, pokud je volba odvoditelné:

![Snímek obrazovky znázorňující zobrazení IntelliSense, pokud je volba odvoditelné](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Pokud je proměnná deklarována jako `Object` , typ za běhu se může změnit během běhu programu. Visual Basic provádí operace označované jako *zabalení* a *rozbalení* pro převod mezi `Object` a hodnotovým typem, což činí provádění pomaleji. Informace o zabalení a rozbalení najdete v tématu [specifikace jazyka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).

Odvození typu se vztahuje na úroveň procedury a neplatí mimo proceduru ve třídě, struktuře, modulu nebo rozhraní.

Další informace naleznete v tématu [odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>Pokud není k dispozici příkaz k odvození možnosti

Pokud zdrojový kód neobsahuje `Option Infer` příkaz, je použita **možnost odvodit** nastavení na [stránce kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) . Pokud je použit kompilátor příkazového řádku, je použita možnost kompilátoru [-optioninfer –](../../reference/command-line-compiler/optioninfer.md) .

#### <a name="to-set-option-infer-in-the-ide"></a>Nastavení volby odvoditelné v integrovaném vývojovém prostředí

1. V **Průzkumník řešení**vyberte projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

2. Klikněte na kartu **kompilovat** .

3. Nastavte hodnotu v poli **odvoditelné možnosti** .

Při vytváření nového projektu je **možnost odvodit** nastavení na kartě **kompilovat** nastavena na **možnost odvodit** nastavení v dialogovém okně **výchozí hodnoty VB** . Chcete-li získat přístup k dialogovému oknu **výchozí hodnoty VB** , v nabídce **nástroje** klikněte na možnost **Možnosti**. V dialogovém okně **Možnosti** rozbalte **projekty a řešení**a potom klikněte na **výchozí hodnoty VB**. Výchozí výchozí nastavení ve výchozím nastavení **jazyka VB** je `On` .

#### <a name="to-set-option-infer-on-the-command-line"></a>Nastavení možnosti odvození v příkazovém řádku

Do příkazu **Vbc** zahrňte možnost kompilátoru [-optioninfer –](../../reference/command-line-compiler/optioninfer.md) .

## <a name="default-data-types-and-values"></a>Výchozí datové typy a hodnoty

Následující tabulka popisuje výsledky různých kombinací určení datového typu a inicializátoru v `Dim` příkazu.

|Byl zadán datový typ?|Byl určen inicializátor?|Příklad|Výsledek|
|---|---|---|---|
|Ne|Ne|`Dim qty`|Pokud `Option Strict` je vypnuto (výchozí nastavení), proměnná je nastavena na `Nothing` .<br /><br /> Pokud `Option Strict` je, dojde k chybě při kompilaci.|
|No|Ano|`Dim qty = 5`|Pokud `Option Infer` je zapnuto (výchozí), proměnná převezme datový typ inicializátoru. Viz [odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Pokud `Option Infer` je vypnutý a `Option Strict` je vypnutý, proměnná vezme datový typ `Object` .<br /><br /> Pokud `Option Infer` je vypnutý a `Option Strict` je zapnutý, dojde k chybě při kompilaci.|
|Ano|Ne|`Dim qty As Integer`|Proměnná je inicializována na výchozí hodnotu pro datový typ. Další informace naleznete v tématu [Dim – příkaz](dim-statement.md).|
|Ano|Ano|`Dim qty  As Integer = 5`|Pokud datový typ inicializátoru nelze převést na zadaný datový typ, dojde k chybě při kompilaci.|

## <a name="example"></a>Příklad

Následující příklady ukazují, jak `Option Infer` příkaz umožňuje odvození místního typu.

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, že běhový typ se může lišit, když je proměnná identifikována jako `Object` .

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>Viz také

- [Dim – příkaz](dim-statement.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare – příkaz](option-compare-statement.md)
- [Option Explicit – příkaz](option-explicit-statement.md)
- [Option Strict – příkaz](option-strict-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../reference/command-line-compiler/optioninfer.md)
- [Zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
