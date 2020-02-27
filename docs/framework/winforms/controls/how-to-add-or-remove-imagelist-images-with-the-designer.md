---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628719"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="83b90-102">Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="83b90-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="83b90-103">Obrázky můžete přidat do <xref:System.Windows.Forms.ImageList> komponenty několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="83b90-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="83b90-104">Obrázky můžete přidat velmi rychle pomocí inteligentní značky přidružené k <xref:System.Windows.Forms.ImageList>, nebo Pokud nastavujete několik dalších vlastností <xref:System.Windows.Forms.ImageList>, může být vhodnější přidat obrázky s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83b90-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="83b90-105">Obrázky můžete také přidat pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="83b90-105">You can also add images by using code.</span></span> <span data-ttu-id="83b90-106">Další informace o tom, jak přidat obrázky s kódem, naleznete v tématu [How to: Add and Remove images with model Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="83b90-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="83b90-107">Obvykle naplníte <xref:System.Windows.Forms.ImageList> komponentu obrázky předtím, než je asociována s ovládacím prvkem, ale to není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="83b90-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="83b90-108">Přidání nebo odebrání imagí pomocí okno Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="83b90-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="83b90-109">Vyberte součást <xref:System.Windows.Forms.ImageList> nebo ji přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="83b90-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="83b90-110">V okno Vlastnosti klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.](./media/visual-studio-ellipsis-button.png)) vedle vlastnosti <xref:System.Windows.Forms.ImageList.Images%2A>.</span><span class="sxs-lookup"><span data-stu-id="83b90-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="83b90-111">V **editoru kolekce imagí**klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="83b90-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="83b90-112">Přidání nebo odebrání obrázků pomocí inteligentní značky</span><span class="sxs-lookup"><span data-stu-id="83b90-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="83b90-113">Vyberte součást <xref:System.Windows.Forms.ImageList> nebo ji přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="83b90-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="83b90-114">Klikněte na piktogram akcí návrháře (</span><span class="sxs-lookup"><span data-stu-id="83b90-114">Click the designer actions glyph (</span></span>![Malá černá šipka](./media/designer-actions-glyph.gif)<span data-ttu-id="83b90-116">)</span><span class="sxs-lookup"><span data-stu-id="83b90-116">)</span></span>

3. <span data-ttu-id="83b90-117">V dialogovém okně **úlohy ImageList** vyberte možnost **zvolit obrázky**.</span><span class="sxs-lookup"><span data-stu-id="83b90-117">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="83b90-118">V **editoru kolekce imagí** klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="83b90-118">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="83b90-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="83b90-119">See also</span></span>

- [<span data-ttu-id="83b90-120">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="83b90-120">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="83b90-121">Návod: provádění běžných úloh pomocí akcí návrháře</span><span class="sxs-lookup"><span data-stu-id="83b90-121">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)
- [<span data-ttu-id="83b90-122">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="83b90-122">ImageList Component</span></span>](imagelist-component-windows-forms.md)
