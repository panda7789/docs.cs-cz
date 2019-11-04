---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1767fcff1742f4ad630b4b996c709b7ded53a129
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459196"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="3d5d7-102">Postupy: Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="3d5d7-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="3d5d7-103">Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="3d5d7-104">V sadě Visual Studio přetáhněte ze **sady nástrojů** do formuláře tři ovládací prvky <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="3d5d7-105">Umístěte je blízko k sobě, ale nechte je nezarovnané.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="3d5d7-106">Na **panelu nástrojů**klikněte na ikonu ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="3d5d7-107">(Nepřetáhněte ikonu do formuláře.)</span><span class="sxs-lookup"><span data-stu-id="3d5d7-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="3d5d7-108">Přesuňte ukazatel myši blízko k třem ovládacím prvkům <xref:System.Windows.Forms.Button>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="3d5d7-109">Ukazatel se změní na vlasovou čáru s připojenou ikonou ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="3d5d7-110">Klikněte a podržte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="3d5d7-111">Přetažením ukazatele myši nakreslete obrys ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="3d5d7-112">Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button>ch ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="3d5d7-113">Uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-113">Release the mouse button.</span></span>

   <span data-ttu-id="3d5d7-114">Tři ovládací prvky <xref:System.Windows.Forms.Button> jsou nyní vloženy do ovládacího prvku <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="3d5d7-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d5d7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d5d7-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="3d5d7-116">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="3d5d7-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="3d5d7-117">Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar</span><span class="sxs-lookup"><span data-stu-id="3d5d7-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
