---
title: 'Postupy: přístup ke kolekcím s klíčem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 717ba9cc8605da08701de1bd13d6bc6da1c9b758
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739623"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="082bf-102">Postupy: Přístup ke kolekcím s klíči ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="082bf-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="082bf-103">Jednotlivé položky kolekce můžete přistupovat pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="082bf-103">You can access individual collection items by key.</span></span> <span data-ttu-id="082bf-104">Tato funkce byla přidána do mnoha tříd kolekcí, které obvykle používá aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="082bf-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="082bf-105">V následujícím seznamu jsou uvedeny některé třídy kolekce, které mají přístupné kolekce s klíčem:</span><span class="sxs-lookup"><span data-stu-id="082bf-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="082bf-106">Klíčem přidruženým k položce v kolekci je obvykle název položky.</span><span class="sxs-lookup"><span data-stu-id="082bf-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="082bf-107">Následující postupy ukazují, jak používat třídy kolekcí k provádění běžných úloh.</span><span class="sxs-lookup"><span data-stu-id="082bf-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="082bf-108">Vyhledání a udělení fokusu vnořenému ovládacímu prvku v kolekci ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="082bf-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="082bf-109">Pomocí metod <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> a <xref:System.Windows.Forms.Control.Focus%2A> určete název ovládacího prvku, který se má najít a který se má zaměřit na.</span><span class="sxs-lookup"><span data-stu-id="082bf-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="082bf-110">Přístup k obrázku v kolekci imagí</span><span class="sxs-lookup"><span data-stu-id="082bf-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="082bf-111">Pomocí vlastnosti <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> zadejte název bitové kopie, ke které chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="082bf-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="082bf-112">Nastavení stránky tabulátoru jako vybrané karty</span><span class="sxs-lookup"><span data-stu-id="082bf-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="082bf-113">Pomocí vlastnosti <xref:System.Windows.Forms.TabControl.SelectedTab%2A> spolu s vlastností <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> určete název stránky karty, která se má nastavit jako vybraná karta.</span><span class="sxs-lookup"><span data-stu-id="082bf-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="082bf-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="082bf-114">See also</span></span>

- [<span data-ttu-id="082bf-115">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="082bf-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="082bf-116">Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="082bf-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
