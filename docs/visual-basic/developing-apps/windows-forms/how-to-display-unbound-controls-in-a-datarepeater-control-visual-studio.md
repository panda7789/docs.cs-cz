---
title: "Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="abd2f-102">Postupy: Zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="abd2f-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="abd2f-103">Kromě vázané ovládací prvky, můžete přidat další ovládací prvky na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, jako jsou například statické štítek nebo obrázek, který se opakuje pro každou položku v <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="abd2f-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd2f-104">Je také nutné mít alespoň jeden prvek vázané <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> nebo nezobrazí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="abd2f-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="abd2f-105">Přidání nevázaných ovládacích prvků DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abd2f-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="abd2f-106">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="abd2f-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="abd2f-107">Přetáhněte obslužné rutiny pro změnu velikosti a pozice na velikost a umístění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="abd2f-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="abd2f-108">Můžete také upravit velikost a umístění ovládacího prvku tak, že změníte **velikost** a **pozice** vlastnosti v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="abd2f-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="abd2f-109">Přidejte alespoň jeden ovládací prvek vázané na data do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="abd2f-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="abd2f-110">Další informace najdete v tématu [postupy: zobrazení vázaný dat v ovládacím prvku DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="abd2f-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="abd2f-111">Přetáhněte ovládací prvek z **sada nástrojů** na oblast šablony položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="abd2f-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="abd2f-112">Všimněte si, že ovládací prvek má dvě obdélníková oblasti.</span><span class="sxs-lookup"><span data-stu-id="abd2f-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="abd2f-113">Vnitřní oblast je *šablony položky*; ovládací prvky přidat do šablony budou opakovat v jednotlivé položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku za běhu.</span><span class="sxs-lookup"><span data-stu-id="abd2f-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="abd2f-114">Vnější oblast je *zobrazení*, kde se zobrazí položky; ovládací prvky, které jsou přidány do této oblasti se nezobrazí v době běhu.</span><span class="sxs-lookup"><span data-stu-id="abd2f-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd2f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="abd2f-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="abd2f-116">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abd2f-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="abd2f-117">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abd2f-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="abd2f-118">Postupy: zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abd2f-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="abd2f-119">Postupy: vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="abd2f-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="abd2f-120">Postupy: Změna vzhledu ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="abd2f-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
