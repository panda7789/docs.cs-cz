---
title: 'Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: be17d5e6a12824c1c9edc867c99e77a6a1437a36
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658586"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="26565-102">Postupy: Přidávání a odebírání obrázků ImageList pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="26565-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="26565-103">Obrázky můžete přidat do <xref:System.Windows.Forms.ImageList> komponenty několika různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="26565-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="26565-104">Obrázky můžete přidat velmi rychle pomocí inteligentní značky přidružené <xref:System.Windows.Forms.ImageList>k, nebo Pokud nastavujete několik dalších vlastností <xref:System.Windows.Forms.ImageList>na, může být vhodnější přidat obrázky s okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26565-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="26565-105">Obrázky můžete také přidat pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="26565-105">You can also add images by using code.</span></span> <span data-ttu-id="26565-106">Další informace o tom, jak přidat obrázky s kódem, naleznete [v tématu How to: Přidejte nebo odeberte obrázky s komponentou](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)model Windows Forms ImageList.</span><span class="sxs-lookup"><span data-stu-id="26565-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="26565-107">Obvykle naplníte <xref:System.Windows.Forms.ImageList> komponentu obrázky předtím, než je přidružena k ovládacímu prvku, ale to není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="26565-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="26565-108">Přidání nebo odebrání imagí pomocí okno Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="26565-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="26565-109"><xref:System.Windows.Forms.ImageList> Vyberte součást nebo ji přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="26565-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="26565-110">V okno Vlastnosti klikněte na tlačítko se třemi tečkami![(tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/visual-studio-ellipsis-button.png)Studio.) vedle <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="26565-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="26565-111">V **editoru kolekce imagí**klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="26565-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="26565-112">Přidání nebo odebrání obrázků pomocí inteligentní značky</span><span class="sxs-lookup"><span data-stu-id="26565-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="26565-113"><xref:System.Windows.Forms.ImageList> Vyberte součást nebo ji přidejte do formuláře.</span><span class="sxs-lookup"><span data-stu-id="26565-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="26565-114">Klikněte na glyf inteligentních značek (![inteligentní značky glyf](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")).</span><span class="sxs-lookup"><span data-stu-id="26565-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="26565-115">V dialogovém okně **úlohy ImageList** vyberte možnost **zvolit obrázky**.</span><span class="sxs-lookup"><span data-stu-id="26565-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="26565-116">V **editoru kolekce imagí** klikněte na **Přidat** nebo **Odebrat** a přidejte nebo odeberte obrázky ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="26565-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="26565-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26565-117">See also</span></span>

- [<span data-ttu-id="26565-118">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="26565-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="26565-119">Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="26565-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="26565-120">Komponenta ImageList</span><span class="sxs-lookup"><span data-stu-id="26565-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)
