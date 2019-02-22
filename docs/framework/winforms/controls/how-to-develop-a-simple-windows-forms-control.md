---
title: 'Postupy: Vývoj ovládacího prvku jednoduchého Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 36891a5acbb2fe06b4ab61573e26612927587c01
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583833"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Postupy: Vývoj ovládacího prvku jednoduchého Windows Forms
Tato část vás provede základní kroky pro vytváření vlastního ovládacího prvku Windows Forms. Jednoduché ovládací prvek vytvořili v tomto návodu umožňuje zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost změnit. Nelze vyvolat nebo zpracování událostí.  
  
### <a name="to-create-a-simple-custom-control"></a>Chcete-li vytvořit jednoduché vlastního ovládacího prvku  
  
1.  Definujte třídu, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  Definujte vlastnosti. (Není nutné definovat vlastnosti, protože dědí mnoho vlastnosti z ovládacího prvku <xref:System.Windows.Forms.Control> třídy, ale většina vlastních ovládacích prvků obecně definovat další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment` , který `FirstControl` používá k formátování zobrazení <xref:System.Windows.Forms.Control.Text%2A> dědí vlastnosti z <xref:System.Windows.Forms.Control>. Další informace o definování vlastností najdete v tématu [přehled vlastností](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Když nastavíte vlastnost, která změní visual zobrazení ovládacího prvku, je nutné vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> metoda překreslení ovládacího prvku. <xref:System.Windows.Forms.Control.Invalidate%2A> je definován v základní třídě <xref:System.Windows.Forms.Control>.  
  
3.  Přepsat chráněnou <xref:System.Windows.Forms.Control.OnPaint%2A> metody zděděné z <xref:System.Windows.Forms.Control> k poskytování logiky vykreslování do ovládacího prvku. Pokud jste nesmí být přepsána <xref:System.Windows.Forms.Control.OnPaint%2A>, nebude možné vykreslit ovládací prvek. V následující fragment kódu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zobrazí <xref:System.Windows.Forms.Control.Text%2A> dědí vlastnosti z <xref:System.Windows.Forms.Control> se zarovnáním určené `alignmentValue` pole.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Zadejte atributy pro ovládací prvek. Atributy umožňují vizuálního návrháře pro zobrazení ovládacího prvku a jeho vlastnosti a události odpovídajícím způsobem v době návrhu. Následující fragment kódu se vztahuje atributů, které mají `TextAlignment` vlastnost. V návrháři, jako je Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atribut (viz část kódu) způsobí, že vlastnost má být zobrazen v rámci logických kategorií. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atribut způsobí, že popisný řetězec, který se zobrazí v dolní části **vlastnosti** okno při `TextAlignment` vybrána vlastnost. Další informace o atributech najdete v tématu [atributy doby návrhu pro komponenty](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (volitelné) Poskytněte zdroje informací pro ovládací prvek. Prostředek, jako je například rastrový obrázek, můžete zadat pro ovládací prvek pomocí možnosti kompilátoru (`/res` pro jazyk C#) pro balíček prostředků pomocí ovládacího prvku. V době běhu, prostředek se dá načíst pomocí metody <xref:System.Resources.ResourceManager> třídy. Další informace o vytváření a používání prostředků najdete v článku [prostředky v desktopových aplikací](../../../../docs/framework/resources/index.md).  
  
6.  Zkompilujte a nasaďte svůj ovládací prvek. Ke kompilaci a nasazení `FirstControl,` proveďte následující kroky:  
  
    1.  Uložte kód v následujícím příkladu do zdrojového souboru (například FirstControl.cs nebo FirstControl.vb).  
  
    2.  Zdrojový kód zkompilovat do sestavení a uložte ho v adresáři vaší aplikace. K tomu, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` – Možnost kompilátoru instruuje kompilátor, že je sestavení při vytváření knihovny (a ne spustitelného souboru). `/out` Možnost určuje cestu a název sestavení. `/r` Možnost poskytuje název sestavení, na které odkazuje váš kód. V tomto příkladu vytvoříte privátní sestavení, které můžete použít jenom vaše aplikace. Proto budete muset uložit v adresáři vaší aplikace. Další informace o vytváření balíčků a nasazení ovládacího prvku pro distribuci, naleznete v tématu [nasazení](../../../../docs/framework/deployment/index.md).  
  
 Následující příklad ukazuje kód pro `FirstControl`. Ovládací prvek je uzavřena v oboru názvů `CustomWinControls`. Obor názvů poskytuje logické seskupení souvisejících typů. Můžete vytvořit ovládací prvek v nové nebo existující obor názvů. V jazyce C# `using` deklarace (v jazyce Visual Basic `Imports`) umožňuje typů přístupný z oboru názvů bez použití plně kvalifikovaný název typu. V následujícím příkladu `using` deklarace umožňuje kódu ke třídě přistupovat <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> stručně <xref:System.Windows.Forms.Control> místo nutnosti použít plně kvalifikovaný název <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>Použití vlastního ovládacího prvku ve formuláři  
 Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`. Vytvoří tři instance `FirstControl`, každý s jinou hodnotou `TextAlignment` vlastnost.  
  
#### <a name="to-compile-and-run-this-sample"></a>Kompilace a spuštění této ukázky  
  
1.  Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms.vb).  
  
2.  Spuštěním následujícího příkazu z adresáře, který obsahuje zdrojový soubor Zkompilujte zdrojový kód do spustitelného souboru sestavení.  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll je sestavení, které obsahuje třídu `FirstControl`. Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro formulář k přístupu (SimpleForm.cs nebo SimpleForms.vb).  
  
3.  Spusťte SimpleForm.exe pomocí následujícího příkazu.  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>Viz také:
- [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
