---
title: Vývoj jednoduchého ovládacího prvku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 5383cee5358dbd260fc6c023d3db607da6b10ea4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742254"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms

V této části se seznámíte se základními kroky při vytváření vlastního ovládacího prvku model Windows Forms. Jednoduchý ovládací prvek vyvinutý v tomto návodu umožňuje změnit zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastností. Nevyvolává ani nezpracovává události.

### <a name="to-create-a-simple-custom-control"></a>Vytvoření jednoduchého vlastního ovládacího prvku

1. Definujte třídu, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Definujte vlastnosti. (Nemusíte definovat vlastnosti, protože ovládací prvek dědí mnoho vlastností z <xref:System.Windows.Forms.Control> třídy, ale většina vlastních ovládacích prvků obecně definuje další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment`, kterou `FirstControl` používá k formátování zobrazení vlastnosti <xref:System.Windows.Forms.Control.Text%2A> zděděné ze <xref:System.Windows.Forms.Control>. Další informace o definování vlastností najdete v tématu [Přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Když nastavíte vlastnost, která změní vizuální zobrazení ovládacího prvku, je nutné vyvolat metodu <xref:System.Windows.Forms.Control.Invalidate%2A> pro překreslení ovládacího prvku. <xref:System.Windows.Forms.Control.Invalidate%2A> je definována v základní třídě <xref:System.Windows.Forms.Control>.

3. Přepsat chráněnou <xref:System.Windows.Forms.Control.OnPaint%2A> metodu zděděnou z <xref:System.Windows.Forms.Control> a poskytnout tak pro svůj ovládací prvek logiku vykreslování. Pokud nepřepisujete <xref:System.Windows.Forms.Control.OnPaint%2A>, ovládací prvek nebude moci nakreslit sám sebe. V následujícím fragmentu kódu <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda zobrazuje vlastnost <xref:System.Windows.Forms.Control.Text%2A> zděděná z <xref:System.Windows.Forms.Control> s zarovnáním zadaným v poli `alignmentValue`.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Zadejte atributy pro svůj ovládací prvek. Atributy umožňují vizuálnímu návrháři zobrazit ovládací prvek a jeho vlastnosti a události odpovídajícím způsobem v době návrhu. Následující fragment kódu používá atributy na vlastnost `TextAlignment`. V návrháři, jako je například Visual Studio, atribut <xref:System.ComponentModel.CategoryAttribute.Category%2A> (zobrazený v fragmentu kódu) způsobí, že se vlastnost zobrazí v rámci logické kategorie. Atribut <xref:System.ComponentModel.DescriptionAttribute.Description%2A> způsobí, že se popisný řetězec zobrazí v dolní části okna **vlastnosti** , když je vybrána vlastnost `TextAlignment`. Další informace o atributech naleznete v tématu [atributy doby návrhu pro součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. volitelné Poskytněte prostředky pro váš ovládací prvek. Můžete poskytnout prostředek, jako je rastrový obrázek, pro váš ovládací prvek pomocí možnosti kompilátoru (`/res` pro C#) k balíčku prostředků s vaším ovládacím prvkem. V době spuštění lze prostředek načíst pomocí metod třídy <xref:System.Resources.ResourceManager>. Další informace o vytváření a používání prostředků najdete v tématu [prostředky v aplikacích klasické pracovní plochy](../../resources/index.md).

6. Zkompilujte a nasaďte svůj ovládací prvek. Pro zkompilování a nasazení `FirstControl,` proveďte následující kroky:

    1. Uložte kód v následující ukázce do zdrojového souboru (například FirstControl.cs nebo FirstControl. vb).

    2. Zkompilujte zdrojový kód do sestavení a uložte ho do adresáře vaší aplikace. Chcete-li to provést, spusťte následující příkaz z adresáře, který obsahuje zdrojový soubor.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         Možnost kompilátoru `/t:library` instruuje kompilátor, že sestavení, které vytváříte, je knihovna (a ne spustitelný soubor). Možnost `/out` Určuje cestu a název sestavení. Možnost`/r` poskytuje název sestavení, na které odkazuje váš kód. V tomto příkladu vytvoříte soukromé sestavení, které může používat pouze vaše aplikace. Proto je nutné jej uložit v adresáři aplikace. Další informace o balení a nasazení ovládacího prvku pro distribuci najdete v tématu [nasazení](../../deployment/index.md).

Následující příklad ukazuje kód pro `FirstControl`. Ovládací prvek je uzavřený v oboru názvů `CustomWinControls`. Obor názvů poskytuje logické seskupení souvisejících typů. Svůj ovládací prvek lze vytvořit v novém nebo existujícím oboru názvů. V C#, deklarace `using` (v Visual Basic, `Imports`) umožňuje k typům pøístup z oboru názvů bez použití plně kvalifikovaného názvu typu. V následujícím příkladu deklarace `using` umožňuje kódu přistupovat ke třídě <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType>, jako jednoduše <xref:System.Windows.Forms.Control> namísto použití plně kvalifikovaného názvu <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Používání vlastního ovládacího prvku na formuláři

Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`. Vytvoří tři instance `FirstControl`, každé s jinou hodnotou pro vlastnost `TextAlignment`.

#### <a name="to-compile-and-run-this-sample"></a>Pro zkompilování a spuštění této ukázky

1. Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms. vb).

2. Zkompilujte zdrojový kód do spustitelného sestavení spuštěním následujícího příkazu z adresáře, který obsahuje zdrojový soubor.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls. dll je sestavení, které obsahuje třídu `FirstControl`. Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro formulář, který k němu přistupuje (SimpleForm.cs nebo SimpleForms. vb).

3. Spusťte SimpleForm. exe pomocí následujícího příkazu.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Viz také

- [Vlastnosti v ovládacích prvcích Windows Forms](properties-in-windows-forms-controls.md)
- [Události v ovládacích prvcích Windows Forms](events-in-windows-forms-controls.md)
