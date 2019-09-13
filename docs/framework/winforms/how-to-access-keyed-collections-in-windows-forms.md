---
title: 'Postupy: Přístup ke kolekcím s klíči ve Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: a88e4766a1e774582bcd0356c9b6e77bc31f1960
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928529"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="2e5f5-102">Postupy: Přístup ke kolekcím s klíči ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e5f5-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="2e5f5-103">Jednotlivé položky kolekce můžete přistupovat pomocí klíče.</span><span class="sxs-lookup"><span data-stu-id="2e5f5-103">You can access individual collection items by key.</span></span> <span data-ttu-id="2e5f5-104">Tato funkce byla přidána do mnoha tříd kolekcí, které obvykle používá aplikace model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2e5f5-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="2e5f5-105">V následujícím seznamu jsou uvedeny některé třídy kolekce, které mají přístupné kolekce s klíčem:</span><span class="sxs-lookup"><span data-stu-id="2e5f5-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="2e5f5-106">Klíčem přidruženým k položce v kolekci je obvykle název položky.</span><span class="sxs-lookup"><span data-stu-id="2e5f5-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="2e5f5-107">Následující postupy ukazují, jak používat třídy kolekcí k provádění běžných úloh.</span><span class="sxs-lookup"><span data-stu-id="2e5f5-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="2e5f5-108">Vyhledání a udělení fokusu vnořenému ovládacímu prvku v kolekci ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="2e5f5-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="2e5f5-109">Pomocí metod <xref:System.Windows.Forms.Control.Focus%2A> a určete název ovládacího prvku, který se má najít a který se má zaměřit na. <xref:System.Windows.Forms.Control.ControlCollection.Find%2A></span><span class="sxs-lookup"><span data-stu-id="2e5f5-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="2e5f5-110">Přístup k obrázku v kolekci imagí</span><span class="sxs-lookup"><span data-stu-id="2e5f5-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="2e5f5-111"><xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> Pomocí vlastnosti zadejte název bitové kopie, ke které chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="2e5f5-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="2e5f5-112">Nastavení stránky tabulátoru jako vybrané karty</span><span class="sxs-lookup"><span data-stu-id="2e5f5-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="2e5f5-113">Pomocí vlastnosti spolu <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> s vlastností zadejte název stránky karty, která se má nastavit jako vybraná karta. <xref:System.Windows.Forms.TabControl.SelectedTab%2A></span><span class="sxs-lookup"><span data-stu-id="2e5f5-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2e5f5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e5f5-114">See also</span></span>

- [<span data-ttu-id="2e5f5-115">Začínáme s Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2e5f5-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="2e5f5-116">Postupy: Přidání nebo odebrání imagí s model Windows Forms komponentou ImageList</span><span class="sxs-lookup"><span data-stu-id="2e5f5-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
