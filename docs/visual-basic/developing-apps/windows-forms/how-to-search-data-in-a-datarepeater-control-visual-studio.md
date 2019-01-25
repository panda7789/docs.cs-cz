---
title: 'Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
ms.openlocfilehash: 514e72afc9570071f57e385574456ff7d716bad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654383"
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="5d0c5-102">Postupy: Vyhledávání dat v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5d0c5-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="5d0c5-103">Při použití <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který obsahuje mnoho záznamů, možná budete chtít umožňují uživatelům vyhledat konkrétní záznam.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="5d0c5-104">Místo vyhledávání dat v samotném ovládacím prvku, lze implementovat hledání pomocí dotazu na <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="5d0c5-105">Pokud se položka nenajde, pak můžete použít <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> vlastnosti vyberte položku a přejděte do zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="5d0c5-106">Implementace hledání</span><span class="sxs-lookup"><span data-stu-id="5d0c5-106">To implement search</span></span>  
  
1.  <span data-ttu-id="5d0c5-107">Přetáhněte <xref:System.Windows.Forms.TextBox> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="5d0c5-108">V okně Vlastnosti změňte **název** vlastnost **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="5d0c5-109">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do formuláře, který obsahuje <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="5d0c5-110">V okně Vlastnosti změňte **název** vlastnost **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="5d0c5-111">Změnit **Text** vlastnost **hledání**.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="5d0c5-112">Dvakrát klikněte <xref:System.Windows.Forms.Button> ovládací prvek, otevře se Editor kódu a přidejte následující kód, který `SearchButton_Click` obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="5d0c5-113">Nahraďte *ProductsBindingSource* názvem <xref:System.Windows.Forms.BindingSource> pro vaše <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>a nahraďte *ProductID* s názvem pole, které chcete vyhledávat.</span><span class="sxs-lookup"><span data-stu-id="5d0c5-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d0c5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d0c5-114">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="5d0c5-115">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5d0c5-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="5d0c5-116">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5d0c5-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="5d0c5-117">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5d0c5-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
