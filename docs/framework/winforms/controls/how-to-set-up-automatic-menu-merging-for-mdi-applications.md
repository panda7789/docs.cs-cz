---
title: 'Postupy: Nastavení automatického slučování nabídek pro aplikace MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533458"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="6b47e-102">Postupy: Nastavení automatického slučování nabídek pro aplikace MDI</span><span class="sxs-lookup"><span data-stu-id="6b47e-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="6b47e-103">Následující postup obsahuje základní kroky pro nastavení automatického slučování v aplikaci rozhraní více dokumentů (MDI) s <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6b47e-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="6b47e-104">Nastavení automatického slučování nabídek</span><span class="sxs-lookup"><span data-stu-id="6b47e-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="6b47e-105">Vytvoření formuláře MDI nadřazené nastavením jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="6b47e-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="6b47e-106">Přidat <xref:System.Windows.Forms.MenuStrip> s nadřazeným MDI nastavení jeho <xref:System.Windows.Forms.Form.MainMenuStrip%2A> s vlastností <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="6b47e-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="6b47e-107">Vytvoření formuláře MDI podřízené a nastavit jeho <xref:System.Windows.Forms.Form.MdiParent%2A> vlastnost na název nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b47e-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="6b47e-108">Přidat <xref:System.Windows.Forms.MenuStrip> podřízené formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="6b47e-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="6b47e-109">Podřízené formuláře nastavena <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `false`.</span><span class="sxs-lookup"><span data-stu-id="6b47e-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="6b47e-110">Přidání položek nabídky pro formulář podřízené <xref:System.Windows.Forms.MenuStrip> , kterou chcete sloučit do nadřazené formuláře <xref:System.Windows.Forms.MenuStrip> při aktivaci podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b47e-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="6b47e-111">Použití <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> vlastnosti v nabídce položky ve formuláři podřízené <xref:System.Windows.Forms.MenuStrip> řídit, jak se sloučit do nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b47e-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b47e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b47e-112">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="6b47e-113">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="6b47e-113">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
