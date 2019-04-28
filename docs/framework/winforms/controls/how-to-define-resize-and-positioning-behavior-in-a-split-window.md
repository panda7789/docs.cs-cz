---
title: 'Postupy: Definování chování změny velikosti a polohování v rozděleném okně'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
ms.openlocfilehash: 8cdcfdfaa135a92ed6a6e96d4a72de2c97f2493d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757622"
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Postupy: Definování chování změny velikosti a polohování v rozděleném okně
Panelů <xref:System.Windows.Forms.SplitContainer> ovládací prvek se přizpůsobují dobře se velikost a manipulovat s uživateli. Ale bude existovat časy, kdy budete chtít programově řídit příčky, kde je umístěn a do jaké míry je možné přesunout.  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost a dalších vlastností <xref:System.Windows.Forms.SplitContainer> ovládací prvek vám poskytnou přesnou kontrolu nad chováním uživatelského rozhraní tak, aby odpovídala vašim potřebám. Tyto vlastnosti jsou uvedeny v následující tabulce.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Vlastnost|Určuje, zda je příčky přesouvatelný prostřednictvím klávesnice nebo myši.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Vlastnost|Určuje vzdálenost v pixelech přesouvatelný příčky od levého nebo horního okraje.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost|Určuje minimální vzdálenost v pixelech, může uživatel přesune příčky.|  
  
 Následující příklad upravuje <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost k vytvoření efektu "přichycení rozdělovač"; když uživatel přetáhne příčky, zvýší v jednotkách 10 pixelů a ne výchozí hodnota 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>Definování chování změny velikosti prvku SplitContainer  
  
1. V postupu, nastavte <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost požadovaná velikost, takže chování "přichycování" příčky je dosaženo.  
  
     V následujícím příkladu kódu v rámci formuláře <xref:System.Windows.Forms.Form.Load> událost, rozdělovač v rámci <xref:System.Windows.Forms.SplitContainer> ovládacího prvku nastavená na jump 10 pixelů při přetažení.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles MyBase.Load  
        Dim splitSnapper as new SplitContainer()  
        splitSnapper.SplitterIncrement = 10  
        splitSnapper.Dock = DockStyle.Fill  
        splitSnapper.Parent = me  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Load(System.Object sender, System.EventArgs e)  
    {  
        SplitContainer splitSnapper = new SplitContainer();  
        splitSnapper.SplitterIncrement = 10;  
        splitSnapper.Dock = DockStyle.Fill;  
        splitSnapper.Parent = this;  
    }  
    ```  
  
     (Visual C#) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Přesunutí příčky mírně doleva nebo doprava nebude mít žádný vliv a jasně; ale při umístění ukazatele myši přejde 10 pixelů v obou směrech, příčky přichycena do nového umístění.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
