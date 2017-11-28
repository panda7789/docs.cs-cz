---
title: "Postupy: Definování chování změny velikosti a polohování v rozděleném okně"
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
- split windows [Windows Forms], resizing
- splitter windows [Windows Forms], resizing
- SplitContainer control [Windows Forms], resizing
ms.assetid: 9bf73f36-ed2d-4a02-b15a-0770eff4fdfa
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db4a99c7dae7783e8ea51f43ad51fcd2214997e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-resize-and-positioning-behavior-in-a-split-window"></a><span data-ttu-id="18210-102">Postupy: Definování chování změny velikosti a polohování v rozděleném okně</span><span class="sxs-lookup"><span data-stu-id="18210-102">How to: Define Resize and Positioning Behavior in a Split Window</span></span>
<span data-ttu-id="18210-103">Panelů <xref:System.Windows.Forms.SplitContainer> řízení samo dobře se po změně velikosti a pracovat s nimi uživatelé.</span><span class="sxs-lookup"><span data-stu-id="18210-103">The panels of the <xref:System.Windows.Forms.SplitContainer> control lend themselves well to being resized and manipulated by users.</span></span> <span data-ttu-id="18210-104">Však bude nastat situace, kdy se má k programovému řízení rozdělovače – kde je umístěný a do jaké míry lze přesunout.</span><span class="sxs-lookup"><span data-stu-id="18210-104">However, there will be times when you will want to programmatically control the splitter—where it is positioned and to what degree it can be moved.</span></span>  
  
 <span data-ttu-id="18210-105"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> Vlastnost a jiné vlastnosti na <xref:System.Windows.Forms.SplitContainer> řízení získáte tak přesné kontrolu nad chováním uživatelského rozhraní tak, aby vyhovovala vašim potřebám.</span><span class="sxs-lookup"><span data-stu-id="18210-105">The <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property and the other properties on the <xref:System.Windows.Forms.SplitContainer> control give you precise control over the behavior of your user interface to suit your needs.</span></span> <span data-ttu-id="18210-106">Tyto vlastnosti jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="18210-106">These properties are listed in the following table.</span></span>  
  
|<span data-ttu-id="18210-107">Název</span><span class="sxs-lookup"><span data-stu-id="18210-107">Name</span></span>|<span data-ttu-id="18210-108">Popis</span><span class="sxs-lookup"><span data-stu-id="18210-108">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="18210-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="18210-109"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="18210-110">Určuje, zda rozdělovače mobilní prostřednictvím klávesnici nebo myš.</span><span class="sxs-lookup"><span data-stu-id="18210-110">Determines if the splitter is movable by means of the keyboard or mouse.</span></span>|  
|<span data-ttu-id="18210-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="18210-111"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="18210-112">Určuje vzdálenost v pixelech od levého nebo horního okraje mobilní dělicí panel.</span><span class="sxs-lookup"><span data-stu-id="18210-112">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="18210-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>Vlastnost</span><span class="sxs-lookup"><span data-stu-id="18210-113"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="18210-114">Určuje minimální vzdálenost v pixelech, že rozdělovače lze přesunout uživatelem.</span><span class="sxs-lookup"><span data-stu-id="18210-114">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
  
 <span data-ttu-id="18210-115">Následující příklad změní <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost vytvořit efekt "uchycení rozdělovače"; když uživatel nastavuje tažením rozdělovače, navýší v jednotkách 10 pixelů a ne výchozí hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="18210-115">The example below modifies the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to create a "snapping splitter" effect; when the user drags the splitter, it increments in units of 10 pixels rather than the default 1.</span></span>  
  
### <a name="to-define-splitcontainer-resize-behavior"></a><span data-ttu-id="18210-116">K definování chování změny velikosti SplitContainer</span><span class="sxs-lookup"><span data-stu-id="18210-116">To define SplitContainer resize behavior</span></span>  
  
1.  <span data-ttu-id="18210-117">V postupu, nastavte <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> vlastnost na požadovanou velikost, takže se dosáhne 'uchycení' chování rozdělovače.</span><span class="sxs-lookup"><span data-stu-id="18210-117">In a procedure, set the <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property to the desired size, so that the 'snapping' behavior of the splitter is achieved.</span></span>  
  
     <span data-ttu-id="18210-118">V následujícím příkladu kódu v rámci formuláře <xref:System.Windows.Forms.Form.Load> událost, rozdělovače v rámci <xref:System.Windows.Forms.SplitContainer> řízení je nastavené na Přejít 10 pixelů při přetažení.</span><span class="sxs-lookup"><span data-stu-id="18210-118">In the following code example, within the form's <xref:System.Windows.Forms.Form.Load> event, the splitter within the <xref:System.Windows.Forms.SplitContainer> control is set to jump 10 pixels when dragged.</span></span>  
  
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
  
     <span data-ttu-id="18210-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="18210-119">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
     <span data-ttu-id="18210-120">Přesun rozdělovače mírně doleva nebo doprava nebude mít žádný účinek a jasně; ale když ukazatel myši přejde 10 pixelů v obou směrech, rozdělovače přichyceno do nového umístění.</span><span class="sxs-lookup"><span data-stu-id="18210-120">Moving the splitter slightly to the left or right will have no discernible effect; however, when the mouse pointer goes 10 pixels in either direction, the splitter will snap to the new position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18210-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="18210-121">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 <xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>
