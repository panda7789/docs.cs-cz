---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: c85e55b6aef45eea65e6f82269375f80acf71017
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527671"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="9bfce-102">Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="9bfce-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="9bfce-103">Můžete přidat Image do <xref:System.Windows.Forms.ImageList> součástí několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="9bfce-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="9bfce-104">Bitové kopie můžete přidat velmi rychle pomocí inteligentních značek přidružené <xref:System.Windows.Forms.ImageList>, nebo pokud nastavujete na několik dalších vlastností <xref:System.Windows.Forms.ImageList>, možná bude jednodušší přidat bitové kopie v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9bfce-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="9bfce-105">Můžete také přidat bitové kopie pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="9bfce-105">You can also add images by using code.</span></span> <span data-ttu-id="9bfce-106">Další informace o tom, jak přidat bitové kopie s kódem najdete v tématu [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="9bfce-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="9bfce-107">Obvykle naplnit <xref:System.Windows.Forms.ImageList> součásti s obrázky, než je přidružena k ovládacímu prvku, ale není to povinné.</span><span class="sxs-lookup"><span data-stu-id="9bfce-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bfce-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="9bfce-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9bfce-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="9bfce-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9bfce-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9bfce-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="9bfce-111">Přidat nebo odebrat pomocí okna Vlastnosti bitové kopie</span><span class="sxs-lookup"><span data-stu-id="9bfce-111">To add or remove images by using the Properties window</span></span>  
  
1.  <span data-ttu-id="9bfce-112">Vyberte <xref:System.Windows.Forms.ImageList> součást, nebo přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="9bfce-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="9bfce-113">V okně vlastností klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9bfce-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3.  <span data-ttu-id="9bfce-114">V **Editor kolekce obrázků**, klikněte na tlačítko **přidat** nebo **odebrat** přidat nebo odebrat ze seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="9bfce-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="9bfce-115">Přidat nebo odebrat obrázky pomocí inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="9bfce-115">To add or remove images using the smart tag</span></span>  
  
1.  <span data-ttu-id="9bfce-116">Vyberte <xref:System.Windows.Forms.ImageList> součást, nebo přidat do formuláře.</span><span class="sxs-lookup"><span data-stu-id="9bfce-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2.  <span data-ttu-id="9bfce-117">Klikněte na inteligentní značky glyfy (![inteligentní značky glyfy](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="9bfce-117">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3.  <span data-ttu-id="9bfce-118">V **ImageList úlohy** dialogové okno, vyberte **zvolte image**.</span><span class="sxs-lookup"><span data-stu-id="9bfce-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4.  <span data-ttu-id="9bfce-119">V **Editor kolekce obrázků** klikněte na tlačítko **přidat** nebo **odebrat** přidat nebo odebrat ze seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="9bfce-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bfce-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bfce-120">See Also</span></span>  
 [<span data-ttu-id="9bfce-121">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="9bfce-121">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="9bfce-122">Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9bfce-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 [<span data-ttu-id="9bfce-123">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="9bfce-123">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
