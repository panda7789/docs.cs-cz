---
title: 'Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730786"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="49c9e-102">Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49c9e-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="49c9e-103">Kromě vázaných ovládacích prvků, můžete chtít přidat další ovládací prvky k <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, jako je statický popisek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="49c9e-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49c9e-104">Také musíte mít alespoň jeden ovládací prvek vázaný <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nebo se nezobrazí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="49c9e-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="49c9e-105">Přidání nevázaných ovládacích prvků DataRepeater</span><span class="sxs-lookup"><span data-stu-id="49c9e-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="49c9e-106">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení z **sady Visual Basic PowerPack** kartu **nástrojů** do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="49c9e-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="49c9e-107">Přetáhněte úchyty velikosti a pozice na velikost a umístění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="49c9e-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="49c9e-108">Můžete také změnit velikost a umístění ovládacího prvku tak, že změníte **velikost** a **pozice** vlastnosti v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="49c9e-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="49c9e-109">Přidejte alespoň jeden ovládací prvek vázaný na data na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="49c9e-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="49c9e-110">Další informace najdete v tématu [jak: Zobrazení vázaných dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="49c9e-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="49c9e-111">Přetáhněte ovládací prvek z **nástrojů** na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="49c9e-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="49c9e-112">Všimněte si, že ovládací prvek má dvě oblasti obdélníkový.</span><span class="sxs-lookup"><span data-stu-id="49c9e-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="49c9e-113">Vnitřní oblasti je *šablony položky*; ovládacích prvků přidaných do šablony se budou opakovat v každé položce <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek v době běhu.</span><span class="sxs-lookup"><span data-stu-id="49c9e-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="49c9e-114">Vnější oblast je *zobrazení*, kde se zobrazí položky; ovládací prvky, které se přidají do této oblasti se nezobrazí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="49c9e-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49c9e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49c9e-115">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="49c9e-116">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="49c9e-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="49c9e-117">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="49c9e-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="49c9e-118">Postupy: Zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="49c9e-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="49c9e-119">Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="49c9e-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [<span data-ttu-id="49c9e-120">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="49c9e-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
