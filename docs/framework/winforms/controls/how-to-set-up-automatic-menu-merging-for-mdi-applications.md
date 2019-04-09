---
title: 'Postupy: Nastavení automatického slučování nabídek pro aplikace MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: 17edde6e3968823abc915eb5faed6d2751ed9393
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129348"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a><span data-ttu-id="55d5f-102">Postupy: Nastavení automatického slučování nabídek pro aplikace MDI</span><span class="sxs-lookup"><span data-stu-id="55d5f-102">How to: Set Up Automatic Menu Merging for MDI Applications</span></span>
<span data-ttu-id="55d5f-103">Následující postup obsahuje základní kroky pro nastavení automatického sloučení v aplikaci rozhraní více dokumentů (MDI) s <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="55d5f-103">The following procedure gives the basic steps for setting up automatic merging in a multiple-document interface (MDI) application with <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
### <a name="to-set-up-automatic-menu-merging"></a><span data-ttu-id="55d5f-104">Nastavení automatického slučování nabídek</span><span class="sxs-lookup"><span data-stu-id="55d5f-104">To set up automatic menu merging</span></span>  
  
1.  <span data-ttu-id="55d5f-105">Vytvořit nadřazený formulář MDI nastavením jeho <xref:System.Windows.Forms.Form.IsMdiContainer%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="55d5f-105">Create the MDI parent form by setting its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2.  <span data-ttu-id="55d5f-106">Přidat <xref:System.Windows.Forms.MenuStrip> na nadřazený objekt MDI, nastavení jeho <xref:System.Windows.Forms.Form.MainMenuStrip%2A> s vlastností <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="55d5f-106">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI parent, setting its <xref:System.Windows.Forms.Form.MainMenuStrip%2A> property to that <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
3.  <span data-ttu-id="55d5f-107">Vytvořit podřízený formulář MDI a nastavte jeho <xref:System.Windows.Forms.Form.MdiParent%2A> nastavte název nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="55d5f-107">Create an MDI child form, and set its <xref:System.Windows.Forms.Form.MdiParent%2A> property to the name of the parent form.</span></span>  
  
4.  <span data-ttu-id="55d5f-108">Přidat <xref:System.Windows.Forms.MenuStrip> na podřízený formulář MDI.</span><span class="sxs-lookup"><span data-stu-id="55d5f-108">Add a <xref:System.Windows.Forms.MenuStrip> to the MDI child form.</span></span>  
  
5.  <span data-ttu-id="55d5f-109">Na podřízeném formuláři, nastavit <xref:System.Windows.Forms.ToolStripItem.Visible%2A> vlastnost <xref:System.Windows.Forms.MenuStrip> k `false`.</span><span class="sxs-lookup"><span data-stu-id="55d5f-109">On the child form, set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `false`.</span></span>  
  
6.  <span data-ttu-id="55d5f-110">Přidání položek nabídky formuláři podřízené <xref:System.Windows.Forms.MenuStrip> , které chcete sloučit do nadřazeného formuláře <xref:System.Windows.Forms.MenuStrip> při aktivaci podřízené formuláře.</span><span class="sxs-lookup"><span data-stu-id="55d5f-110">Add menu items to the child form's <xref:System.Windows.Forms.MenuStrip> that you want to merge into the parent form's <xref:System.Windows.Forms.MenuStrip> when the child form is activated.</span></span>  
  
7.  <span data-ttu-id="55d5f-111">Použití <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> položky vlastnosti v nabídce v podřízeném formuláři <xref:System.Windows.Forms.MenuStrip> řídit, jak se sloučí do nadřazeného formuláře.</span><span class="sxs-lookup"><span data-stu-id="55d5f-111">Use the <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> property on the menu items in the child form's <xref:System.Windows.Forms.MenuStrip> to control how they merge into the parent form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d5f-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55d5f-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="55d5f-113">Přehled ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="55d5f-113">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
