---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: 732267b431c5058fa7039f0fb132e6161c37d4a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303125"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="dfb5a-102">Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="dfb5a-102">How to: Add or Remove ImageList Images with the Designer</span></span>
<span data-ttu-id="dfb5a-103">Můžete přidat Image do <xref:System.Windows.Forms.ImageList> součástí několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="dfb5a-104">Lze také přidat obrázky velmi rychle s využitím inteligentních značek přidružené <xref:System.Windows.Forms.ImageList>, nebo pokud nastavujete na několik dalších vlastností <xref:System.Windows.Forms.ImageList>, pravděpodobně pro vás bude pohodlnější přidání imagí pomocí okna Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="dfb5a-105">Můžete také přidat obrázky pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-105">You can also add images by using code.</span></span> <span data-ttu-id="dfb5a-106">Další informace o tom, jak přidat obrázky s kódem, najdete v části [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="dfb5a-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="dfb5a-107">Obvykle naplnit <xref:System.Windows.Forms.ImageList> komponentu s obrázky předtím, než je přidružena k ovládacímu prvku, ale tento krok není povinný.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfb5a-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="dfb5a-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="dfb5a-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="dfb5a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="dfb5a-111">K přidávání a odebírání obrázků pomocí okna Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dfb5a-111">To add or remove images by using the Properties window</span></span>  
  
1. <span data-ttu-id="dfb5a-112">Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-112">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2. <span data-ttu-id="dfb5a-113">V okně Vlastnosti klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](../media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-113">In the Properties window, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
3. <span data-ttu-id="dfb5a-114">V **Editor kolekce obrázků**, klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-114">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="dfb5a-115">Přidání nebo odebrání obrázků s využitím inteligentních značek</span><span class="sxs-lookup"><span data-stu-id="dfb5a-115">To add or remove images using the smart tag</span></span>  
  
1. <span data-ttu-id="dfb5a-116">Vyberte <xref:System.Windows.Forms.ImageList> komponenty, nebo přidejte jej do formuláře.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-116">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>  
  
2. <span data-ttu-id="dfb5a-117">Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="dfb5a-117">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>  
  
3. <span data-ttu-id="dfb5a-118">V **ImageList úlohy** dialogu **zvolte image**.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-118">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>  
  
4. <span data-ttu-id="dfb5a-119">V **Editor kolekce Images** klikněte na tlačítko **přidat** nebo **odebrat** k přidávání a odebírání obrázků ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="dfb5a-119">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb5a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfb5a-120">See also</span></span>

- [<span data-ttu-id="dfb5a-121">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="dfb5a-121">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="dfb5a-122">Návod: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="dfb5a-122">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="dfb5a-123">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="dfb5a-123">ImageList Component</span></span>](imagelist-component-windows-forms.md)
