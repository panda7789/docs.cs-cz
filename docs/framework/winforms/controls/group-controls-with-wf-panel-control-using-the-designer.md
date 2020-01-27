---
title: Seskupení ovládacích prvků pomocí ovládacího prvku panel pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 927aeb5b51bc1ac4e22a45e487b49424b4e67b71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745651"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="fe29b-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="fe29b-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="fe29b-103">Ovládací prvky <xref:System.Windows.Forms.Panel> model Windows Forms slouží k seskupení dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="fe29b-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="fe29b-104">Existují tři důvody pro seskupení ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="fe29b-104">There are three reasons to group controls.</span></span> <span data-ttu-id="fe29b-105">Jedním z nich je vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní; Další je programové seskupení přepínačů, například. Poslední je pro přesunutí ovládacích prvků jako jednotky v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="fe29b-106">Vytvoření skupiny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="fe29b-106">To create a group of controls</span></span>

1. <span data-ttu-id="fe29b-107">Přetáhněte ovládací prvek <xref:System.Windows.Forms.Panel> z karty **model Windows Forms** panelu nástrojů na formulář.</span><span class="sxs-lookup"><span data-stu-id="fe29b-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="fe29b-108">Do panelu přidejte další ovládací prvky, nakreslením každé dovnitř panelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="fe29b-109">Pokud máte ovládací prvky, které chcete uzavřít na panelu, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat ovládací prvek <xref:System.Windows.Forms.Panel> a pak je vložit do panelu.</span><span class="sxs-lookup"><span data-stu-id="fe29b-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="fe29b-110">Můžete je také přetáhnout na panel.</span><span class="sxs-lookup"><span data-stu-id="fe29b-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="fe29b-111">Volitelné Chcete-li přidat ohraničení panelu, nastavte jeho vlastnost <xref:System.Windows.Forms.BorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="fe29b-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="fe29b-112">Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>a <xref:System.Windows.Forms.BorderStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="fe29b-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="fe29b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe29b-113">See also</span></span>

- [<span data-ttu-id="fe29b-114">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="fe29b-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="fe29b-115">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="fe29b-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="fe29b-116">Postupy: Nastavení pozadí panelu</span><span class="sxs-lookup"><span data-stu-id="fe29b-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
