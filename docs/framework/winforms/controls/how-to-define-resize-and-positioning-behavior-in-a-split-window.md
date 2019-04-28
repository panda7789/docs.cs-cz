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
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="8f2c6-102">Postupy: Definování chování změny velikosti a polohování v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="8f2c6-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="8f2c6-103">Panelů <xref:System.Windows.Forms.SplitContainer> ovládací prvek se přizpůsobují dobře se velikost a manipulovat s uživateli.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="8f2c6-104">Ale bude existovat časy, kdy budete chtít programově řídit příčky, kde je umístěn a do jaké míry je možné přesunout.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="8f2c6-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost a dalších vlastností <xref:System.Windows.Forms.SplitContainer> ovládací prvek vám poskytnou přesnou kontrolu nad chováním uživatelského rozhraní tak, aby odpovídala vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="8f2c6-106">Tyto vlastnosti jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="8f2c6-107">Název</span><span class="sxs-lookup"><span data-stu-id="8f2c6-107">Name</span></span>|<span data-ttu-id="8f2c6-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8f2c6-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="8f2c6-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8f2c6-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="8f2c6-110">Určuje, zda je příčky přesouvatelný prostřednictvím klávesnice nebo myši.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="8f2c6-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8f2c6-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="8f2c6-112">Určuje vzdálenost v pixelech přesouvatelný příčky od levého nebo horního okraje.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="8f2c6-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost</span><span class="sxs-lookup"><span data-stu-id="8f2c6-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="8f2c6-114">Určuje minimální vzdálenost v pixelech, může uživatel přesune příčky.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="8f2c6-115">Následující příklad upravuje <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost k vytvoření efektu "přichycení rozdělovač"; když uživatel přetáhne příčky, zvýší v jednotkách 10 pixelů a ne výchozí hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="8f2c6-116">Definování chování změny velikosti prvku SplitContainer</span><span class="sxs-lookup"><span data-stu-id="8f2c6-116">To define SplitContainer resize behavior</span></span>  
  
1. <span data-ttu-id="8f2c6-117">V postupu, nastavte <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost požadovaná velikost, takže chování "přichycování" příčky je dosaženo.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="8f2c6-118">V následujícím příkladu kódu v rámci formuláře <xref:System.Windows.Forms.Form.Load> událost, rozdělovač v rámci <xref:System.Windows.Forms.SplitContainer> ovládacího prvku nastavená na jump 10 pixelů při přetažení.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
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
  
     <span data-ttu-id="8f2c6-119">(Visual C#) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-119">(Visual C#) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="8f2c6-120">Přesunutí příčky mírně doleva nebo doprava nebude mít žádný vliv a jasně; ale při umístění ukazatele myši přejde 10 pixelů v obou směrech, příčky přichycena do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="8f2c6-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2c6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f2c6-121">See also</span></span>

- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
