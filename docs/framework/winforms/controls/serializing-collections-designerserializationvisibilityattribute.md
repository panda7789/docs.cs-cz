---
title: 'Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
ms.openlocfilehash: a502ecc30911f2296bf48eaa195f5b6452b7588a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute
Vlastní ovládací prvky někdy zveřejní kolekci jako vlastnost. Tento návod ukazuje, jak používat <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třída řídit, jak je kolekce serializovat v době návrhu. Použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> hodnotu pro vlastnost vaší kolekce zajistí, že vlastnost budou serializována.  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: serializace kolekcí z standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>Vytvoření ovládacího prvku, který má serializovatelný kolekci  
 Prvním krokem je vytvoření ovládacího prvku, který má kolekci serializovatelný jako vlastnost. Můžete upravit obsah této kolekce pomocí **Editor kolekce**, kterým můžete přistupovat z **vlastnosti** okno.  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>Vytvoření ovládacího prvku s serializovatelný kolekcí  
  
1.  Vytvoření projektu knihovny ovládacích prvků Windows názvem `SerializationDemoControlLib`. Další informace najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).  
  
2.  Přejmenování `UserControl1` k `SerializationDemoControl`. Další informace najdete v tématu [postupy: přejmenování identifikátory](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).  
  
3.  V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnost `10`.  
  
4.  Místní <xref:System.Windows.Forms.TextBox> řídit ve `SerializationDemoControl`.  
  
5.  Vyberte <xref:System.Windows.Forms.TextBox> ovládacího prvku. V **vlastnosti** nastavte následující vlastnosti.  
  
    |Vlastnost|Změňte na|  
    |--------------|---------------|  
    |**Víceřádkového výrazu**|`true`|  
    |**Ukotvení**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**Posuvníky**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  V **Editor kódu**, deklarovat pole řetězce pole s názvem `stringsValue` v `SerializationDemoControl`.  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  Definování `Strings` vlastnost `SerializationDemoControl`.  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota slouží k povolení serializace kolekce.  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.  
  
2.  Najít `Strings` vlastnost <xref:System.Windows.Forms.PropertyGrid> z **UserControl – kontejner testů**. Klikněte na tlačítko `Strings` vlastnost, pak klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězec**.  
  
3.  Zadejte několik řetězců v **Editor kolekce řetězec**. Oddělte je stisknutím klávesy ENTER na konci každé řetězec. Klikněte na tlačítko **OK** při zadání řetězce.  
  
> [!NOTE]
>  Zobrazí řetězce, které jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
## <a name="serializing-a-collection-property"></a>Serializace vlastnost kolekce  
 Chcete-li otestovat serializace chování ovládacího prvku, bude umístění ve formuláři a změňte obsah kolekce s **Editor kolekce**. Zobrazí stav serializovaných kolekce prohlížením speciální návrháře souboru, do kterého **Návrhář formulářů Windows** vysílá kódu.  
  
#### <a name="to-serialize-a-collection"></a>K serializaci kolekce  
  
1.  Přidejte projekt aplikace Windows k řešení. Název projektu `SerializationDemoControlTest`.  
  
2.  V **sada nástrojů**, najít na kartě s názvem **SerializationDemoControlLib součásti**. Na této kartě můžete najít `SerializationDemoControl`. Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).  
  
3.  Místní `SerializationDemoControl` ve formuláři.  
  
4.  Najít `Strings` vlastnost **vlastnosti** okno. Klikněte na tlačítko `Strings` vlastnost, pak klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězec**.  
  
5.  Zadejte několik řetězců v **Editor kolekce řetězec**. Oddělte je stisknutím klávesy ENTER na konci každé řetězec. Klikněte na tlačítko **OK** při zadání řetězce.  
  
> [!NOTE]
>  Zobrazí řetězce, které jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.  
  
1.  V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.  
  
2.  Otevřete **Form1** uzlu. Ybrat je do souboru s názvem **Form1.Designer.cs** nebo **Form1.Designer.vb**. Toto je soubor, do kterého **Návrhář formulářů Windows** vysílá kód představující stav návrhu a jeho podřízených ovládacích prvků formuláře. Otevřete tento soubor **Editor kódu**.  
  
3.  Otevřete oblast názvem **Windows Form Designer generovaného kódu** a najděte část s názvem bez přípony **serializationDemoControl1**. Pod tímto štítkem je kód představující serializovaný stav ovládacího prvku. Zobrazí řetězce, které jste zadali v kroku 5 v přiřazení k `Strings` vlastnost. Následující příklady kódu v C# a Visual Basic, zobrazí podobná co se zobrazí pokud jste zadali řetězce "red", "oranžové" a "žlutý" code.  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  V **Editor kódu**, změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` vlastnost <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. Znovu sestavte řešení a zopakujte kroky 3 a 4.  
  
> [!NOTE]
>  V takovém případě **Návrhář formulářů Windows** vysílá žádné přiřazení `Strings` vlastnost.  
  
## <a name="next-steps"></a>Další kroky  
 Jakmile budete vědět, jak k serializaci kolekce standardní typy, vezměte v úvahu integraci vaše vlastní ovládací prvky hlubšímu do prostředí návrhu. Následující témata popisují postup rozšíření integrace návrhu pro vaše vlastní ovládací prvky:  
  
-   [Architektura pro návrh](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Atributy v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Přehled Návrháře serializace](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [Přehled Návrháře serializace](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
