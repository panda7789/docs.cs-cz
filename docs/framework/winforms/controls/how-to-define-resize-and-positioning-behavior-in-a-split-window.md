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
ms.openlocfilehash: 015e93fb551b8d48b8a57662b8def61c3cb46c2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a>Postupy: Definování chování změny velikosti a polohování v rozděleném okně
Panelů <xref:System.Windows.Forms.SplitContainer> řízení samo dobře se po změně velikosti a pracovat s nimi uživatelé. Však bude nastat situace, kdy se má k programovému řízení rozdělovače – kde je umístěný a do jaké míry lze přesunout.  
  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost a jiné vlastnosti na <xref:System.Windows.Forms.SplitContainer> řízení získáte tak přesné kontrolu nad chováním uživatelského rozhraní tak, aby vyhovovala vašim potřebám. Tyto vlastnosti jsou uvedené v následující tabulce.  
  
|Název|Popis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Vlastnost|Určuje, zda rozdělovače mobilní prostřednictvím klávesnici nebo myš.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Vlastnost|Určuje vzdálenost v pixelech od levého nebo horního okraje mobilní dělicí panel.|  
|<xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost|Určuje minimální vzdálenost v pixelech, že rozdělovače lze přesunout uživatelem.|  
  
 Následující příklad změní <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost vytvořit efekt "uchycení rozdělovače"; když uživatel nastavuje tažením rozdělovače, navýší v jednotkách 10 pixelů a ne výchozí hodnota 1.  
  
### <a name="to-define-splitcontainer-resize-behavior"></a>K definování chování změny velikosti SplitContainer  
  
1.  V postupu, nastavte <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost na požadovanou velikost, takže se dosáhne 'uchycení' chování rozdělovače.  
  
     V následujícím příkladu kódu v rámci formuláře <xref:System.Windows.Forms.Form.Load> událost, rozdělovače v rámci <xref:System.Windows.Forms.SplitContainer> řízení je nastavené na Přejít 10 pixelů při přetažení.  
  
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
  
     (Visual C#) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     Přesun rozdělovače mírně doleva nebo doprava nebude mít žádný účinek a jasně; ale když ukazatel myši přejde 10 pixelů v obou směrech, rozdělovače přichyceno do nového umístění.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
