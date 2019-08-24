---
title: 'Postupy: Přiřazení existujících ovládacích prvků jinému nadřazenému prvku'
ms.date: 03/30/2017
helpviewer_keywords:
- container controls [Windows Forms], Windows Forms
- layout [Windows Forms], resizing
- layout [Windows Forms], child controls
ms.assetid: 5a5723ff-34e0-4b6f-a57b-be4ebe35cb34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84e662e0bd2689115abe128c6442e4462eed3e18
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987033"
---
# <a name="how-to-reassign-existing-controls-to-a-different-parent"></a><span data-ttu-id="5fdca-102">Postupy: Opětovné přiřazení existujících ovládacích prvků jinému nadřazenému prvku</span><span class="sxs-lookup"><span data-stu-id="5fdca-102">How to: Reassign existing controls to a different parent</span></span>

<span data-ttu-id="5fdca-103">Ovládací prvky, které existují na formuláři, můžete přiřadit k novému ovládacímu prvku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="5fdca-103">You can assign controls that exist on your form to a new container control.</span></span>

1. <span data-ttu-id="5fdca-104">V sadě Visual Studio přetáhněte tři <xref:System.Windows.Forms.Button> ovládací prvky z **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="5fdca-104">In Visual Studio, drag three <xref:System.Windows.Forms.Button> controls from the **Toolbox** onto the form.</span></span> <span data-ttu-id="5fdca-105">Umístěte je blízko k sobě, ale nechte je nezarovnané.</span><span class="sxs-lookup"><span data-stu-id="5fdca-105">Position them near to each other, but leave them unaligned.</span></span>

2. <span data-ttu-id="5fdca-106">Na **panelu nástrojů**klikněte <xref:System.Windows.Forms.FlowLayoutPanel> na ikonu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5fdca-106">In the **Toolbox**, click the <xref:System.Windows.Forms.FlowLayoutPanel> control icon.</span></span> <span data-ttu-id="5fdca-107">(Nepřetáhněte ikonu do formuláře.)</span><span class="sxs-lookup"><span data-stu-id="5fdca-107">(Do not drag the icon onto the form.)</span></span>

3. <span data-ttu-id="5fdca-108">Přesuňte ukazatel myši blízko k třem <xref:System.Windows.Forms.Button> ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="5fdca-108">Move the mouse pointer close to the three <xref:System.Windows.Forms.Button> controls.</span></span>

   <span data-ttu-id="5fdca-109">Ukazatel se změní na vlasovou čáru s <xref:System.Windows.Forms.FlowLayoutPanel> připojenou ikonou ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5fdca-109">The pointer changes to a crosshair with the <xref:System.Windows.Forms.FlowLayoutPanel> control icon attached.</span></span>

4. <span data-ttu-id="5fdca-110">Klikněte a podržte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="5fdca-110">Click and hold the mouse button.</span></span>

5. <span data-ttu-id="5fdca-111">Přetažením ukazatele myši nakreslete obrys <xref:System.Windows.Forms.FlowLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5fdca-111">Drag the mouse pointer to draw the outline of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="5fdca-112">Vykreslete obrys kolem tří <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="5fdca-112">Draw the outline around the three <xref:System.Windows.Forms.Button> controls.</span></span>

7. <span data-ttu-id="5fdca-113">Uvolněte tlačítko myši.</span><span class="sxs-lookup"><span data-stu-id="5fdca-113">Release the mouse button.</span></span>

   <span data-ttu-id="5fdca-114">Tři <xref:System.Windows.Forms.Button> ovládací prvky jsou nyní vloženy <xref:System.Windows.Forms.FlowLayoutPanel> do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5fdca-114">The three <xref:System.Windows.Forms.Button> controls are now inserted into the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fdca-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fdca-115">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="5fdca-116">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5fdca-116">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="5fdca-117">Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí zarovnávacím čárám</span><span class="sxs-lookup"><span data-stu-id="5fdca-117">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
