---
title: 'Postupy: Přístup kolekcím s klíči ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: af398e8ac051bfc89c532fe5dc216e9cfbfdc4b9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709612"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="c0ca9-102">Postupy: Přístup kolekcím s klíči ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0ca9-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="c0ca9-103">Jednotlivé kolekce položek můžete přistupovat pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-103">You can access individual collection items by key.</span></span> <span data-ttu-id="c0ca9-104">Tato funkce byla přidána k mnoha třídy kolekcí, které jsou obvykle používány aplikací modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="c0ca9-105">V následujícím seznamu jsou uvedeny některé třídy kolekcí, které mají přístupné kolekce s klíči:</span><span class="sxs-lookup"><span data-stu-id="c0ca9-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="c0ca9-106">Klíč přidružený k položce v kolekci je obvykle název položky.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="c0ca9-107">Následující postupy ukazují, jak provádět běžné úlohy pomocí třídy kolekcí.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="c0ca9-108">Najít a fokus se přesune na ovládací prvek vnořené v kolekci ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="c0ca9-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="c0ca9-109">Použití <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> a <xref:System.Windows.Forms.Control.Focus%2A> metody k zadání názvu najít a fokus se přesune do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="c0ca9-110">Pro přístup k obrazu v kolekci obrázků</span><span class="sxs-lookup"><span data-stu-id="c0ca9-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="c0ca9-111">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> vlastnosti a určit název image, které chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="c0ca9-112">Nastavení stránky karty jako vybraná karta</span><span class="sxs-lookup"><span data-stu-id="c0ca9-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="c0ca9-113">Použití <xref:System.Windows.Forms.TabControl.SelectedTab%2A> vlastnost spolu s <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> vlastnosti a určit název stránky karty jako vybraná karta nastavení.</span><span class="sxs-lookup"><span data-stu-id="c0ca9-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c0ca9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0ca9-114">See also</span></span>
- [<span data-ttu-id="c0ca9-115">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0ca9-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="c0ca9-116">Postupy: Přidávání a odebírání obrázků pomocí komponenty Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="c0ca9-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
