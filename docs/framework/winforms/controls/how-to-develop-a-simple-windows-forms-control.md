---
title: "Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da876ec74bf80d4329451a9bf125421731c7f9de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Postupy: Vývoj jednoduchého ovládacího prvku Windows Forms
Tato část vás provede procesem klíčové kroky pro vytvoření vlastního ovládacího prvku Windows Forms. Jednoduché ovládací prvek vyvinuté v tomto návodu umožňuje zarovnání jeho <xref:System.Windows.Forms.Control.Text%2A> vlastnost změnit. Nebudou vyvolat a zpracování událostí.  
  
### <a name="to-create-a-simple-custom-control"></a>Chcete-li vytvořit jednoduché vlastního ovládacího prvku  
  
1.  Definice třídy, která je odvozena z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  Definování vlastností. (Není nutné definovat vlastnosti, protože dědí mnoho vlastnosti z ovládacího prvku <xref:System.Windows.Forms.Control> třídy, ale většina vlastní ovládací prvky obecně definovat další vlastnosti.) Následující fragment kódu definuje vlastnost s názvem `TextAlignment` , `FirstControl` používá k formátování zobrazení <xref:System.Windows.Forms.Control.Text%2A> vlastnost zděděna od <xref:System.Windows.Forms.Control>. Další informace o definování vlastností v tématu [přehled vlastností](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     Když nastavíte vlastnost, která určuje visual zobrazení ovládacího prvku, je nutné vyvolat <xref:System.Windows.Forms.Control.Invalidate%2A> metodu ho překreslit ovládacího prvku. <xref:System.Windows.Forms.Control.Invalidate%2A>je definována v základní třídě <xref:System.Windows.Forms.Control>.  
  
3.  Přepsání chráněného <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zděděno z <xref:System.Windows.Forms.Control> zajistit logiku vykreslování vlastního ovládacího prvku. Pokud není přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A>, vlastní ovládací prvek nebudou mít k vykreslení sám sebe. V následující fragment kódu <xref:System.Windows.Forms.Control.OnPaint%2A> metoda zobrazí <xref:System.Windows.Forms.Control.Text%2A> vlastnost zděděna od <xref:System.Windows.Forms.Control> s zarovnání určeného `alignmentValue` pole.  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  Zadejte atributy pro vlastní ovládací prvek. Atributy povolit vizuálního návrháře správně zobrazit vlastní ovládací prvek a jeho vlastnosti a události v době návrhu. Následující fragment kódu se vztahuje atributy, které mají `TextAlignment` vlastnost. V Návrháři třeba v sadě Visual Studio <xref:System.ComponentModel.CategoryAttribute.Category%2A> atribut (zobrazené ve fragmentu kódu) způsobí, že vlastnost, který se má zobrazit v rámci logické kategorie. <xref:System.ComponentModel.DescriptionAttribute.Description%2A> Atribut způsobuje popisný řetězec, který se má zobrazit v dolní části **vlastnosti** okno při `TextAlignment` vlastnost vybrána. Další informace o atributech najdete v tématu [atributy doby návrhu pro součásti](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3).  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (volitelné) Zadejte prostředky pro vaše ovládací prvek. Prostředek, jako je například rastrový obrázek, můžete zadat pro ovládací prvek pomocí možnosti kompilátoru (`/res` pro jazyk C#) k prostředkům balíček pomocí vlastního ovládacího prvku. V době běhu prostředku se dá načíst pomocí metody <xref:System.Resources.ResourceManager> třídy. Další informace o vytváření a používání prostředků najdete v tématu [prostředků v aplikacích plochy](../../../../docs/framework/resources/index.md).  
  
6.  Kompilace a nasadit vlastní ovládací prvek. Pro zkompilování a nasadit `FirstControl,` provést následující kroky:  
  
    1.  Uložte kód v následující ukázce ke zdrojovému souboru (například FirstControl.cs nebo FirstControl.vb).  
  
    2.  Kompilace zdrojového kódu do sestavení a uložte ho do adresáře vaší aplikace. K tomu, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` – Možnost kompilátoru říká kompilátoru, že je sestavení, kterou vytváříte knihovny (a ne spustitelný soubor). `/out` Možnost určuje cestu a název sestavení. `/r` Možnost poskytuje název sestavení, které jsou odkazovány pomocí kódu. V tomto příkladu vytvoříte privátní sestavení, které můžete použít jenom vaší aplikace. Proto je nutné uložit v adresáři vaší aplikace. Další informace o balení a nasazení ovládacího prvku pro distribuci najdete v tématu [nasazení](../../../../docs/framework/deployment/index.md).  
  
 Následující příklad ukazuje kód pro `FirstControl`. Ovládací prvek je uzavřena v oboru názvů `CustomWinControls`. Obor názvů poskytuje logické seskupení souvisejících typů. Můžete vytvořit vlastní ovládací prvek v nových nebo existujících oboru názvů. V jazyce C# `using` deklarace (v jazyce Visual Basic `Imports`) umožňuje typům přístupná z oboru názvů bez použití plně kvalifikovaný název typu. V následujícím příkladu `using` deklarace umožňuje kód pro přístup k třídě <xref:System.Windows.Forms.Control> z <xref:System.Windows.Forms?displayProperty=nameWithType> jako jednoduše <xref:System.Windows.Forms.Control> místo nutnosti použít plně kvalifikovaný název <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>Pomocí vlastního ovládacího prvku ve formuláři  
 Následující příklad ukazuje jednoduchý formulář, který používá `FirstControl`. Vytvoří tři instance `FirstControl`, každý s jinou hodnotou `TextAlignment` vlastnost.  
  
#### <a name="to-compile-and-run-this-sample"></a>Pro zkompilování a spuštění této ukázky  
  
1.  Uložte kód v následujícím příkladu do zdrojového souboru (SimpleForm.cs nebo SimpleForms.vb).  
  
2.  Kompilace zdrojový kód do spustitelného souboru sestavení tak, že spustíte následující příkaz z adresáře, který obsahuje zdrojový soubor.  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll je sestavení obsahující třídu `FirstControl`. Toto sestavení musí být ve stejném adresáři jako zdrojový soubor pro daný formulář, který přistupuje k (SimpleForm.cs nebo SimpleForms.vb).  
  
3.  Spusťte SimpleForm.exe pomocí následujícího příkazu.  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
