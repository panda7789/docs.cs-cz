---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
ms.openlocfilehash: a65b3c2b596a2d88ce4236aeadd86993bb268aa6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039791"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="e2879-102">Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="e2879-102">How to: Reassign Existing Controls to a Different Parent</span></span>
<span data-ttu-id="e2879-103">Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e2879-103">You can assign controls that exist on your form to a new container control.</span></span>

## <a name="to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="e2879-104">Změna přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="e2879-104">To reassign existing controls to a different parent</span></span>

1. <span data-ttu-id="e2879-105">Přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e2879-105">Drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span>

     <span data-ttu-id="e2879-106">Umístěte je blízko k sobě, ale nechte je nezarovnané.</span><span class="sxs-lookup"><span data-stu-id="e2879-106">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="e2879-107">Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.FlowLayoutPanel> na ikonu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2879-107">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span>

     <span data-ttu-id="e2879-108">Nepřetáhněte ikonu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="e2879-108">Do not drag the icon onto the form.</span></span>

3. <span data-ttu-id="e2879-109">Přesuňte ukazatel myši blízko k třem <xref:System.Windows.Forms.Button> ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="e2879-109">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

     <span data-ttu-id="e2879-110">Ukazatel se změní na vlasovou čáru s <xref:System.Windows.Forms.FlowLayoutPanel> připojenou ikonou ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2879-110">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="e2879-111">Klikněte a podržte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="e2879-111">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="e2879-112">Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2879-112">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="e2879-113">Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e2879-113">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="e2879-114">Uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="e2879-114">Release the mouse button.</span></span>

     <span data-ttu-id="e2879-115">Tři <xref:System.Windows.Forms.Button> ovládací prvky jsou nyní vloženy <xref:System.Windows.Forms.FlowLayoutPanel> do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e2879-115">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="e2879-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2879-116">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="e2879-117">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e2879-117">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="e2879-118">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="e2879-118">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="e2879-119">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám</span><span class="sxs-lookup"><span data-stu-id="e2879-119">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
