---
title: 'Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: cadfa715b140c63b216ec0ca2e6d6a6589ae3458
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040391"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="0ede5-102">Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms Panel pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="0ede5-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="0ede5-103">Ovládací <xref:System.Windows.Forms.Panel> prvky model Windows Forms slouží k seskupení dalších ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0ede5-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="0ede5-104">Existují tři důvody pro seskupení ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0ede5-104">There are three reasons to group controls.</span></span> <span data-ttu-id="0ede5-105">Jedním z nich je vizuální seskupení souvisejících prvků formuláře pro jasné uživatelské rozhraní; Další je programové seskupení přepínačů, například. Poslední je pro přesunutí ovládacích prvků jako jednotky v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="0ede5-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>

## <a name="to-create-a-group-of-controls"></a><span data-ttu-id="0ede5-106">Vytvoření skupiny ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="0ede5-106">To create a group of controls</span></span>

1. <span data-ttu-id="0ede5-107">Přetáhněte ovládací prvek z karty model Windows Forms panelu nástrojů na formulář. <xref:System.Windows.Forms.Panel></span><span class="sxs-lookup"><span data-stu-id="0ede5-107">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>

2. <span data-ttu-id="0ede5-108">Do panelu přidejte další ovládací prvky, nakreslením každé dovnitř panelu.</span><span class="sxs-lookup"><span data-stu-id="0ede5-108">Add other controls to the panel, drawing each inside the panel.</span></span>

     <span data-ttu-id="0ede5-109">Pokud máte ovládací prvky, které chcete uzavřít na panelu, můžete vybrat všechny ovládací prvky, vyjmout je do schránky, vybrat <xref:System.Windows.Forms.Panel> ovládací prvek a pak je vložit do panelu.</span><span class="sxs-lookup"><span data-stu-id="0ede5-109">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="0ede5-110">Můžete je také přetáhnout na panel.</span><span class="sxs-lookup"><span data-stu-id="0ede5-110">You can also drag them into the panel.</span></span>

3. <span data-ttu-id="0ede5-111">Volitelné Chcete-li přidat ohraničení panelu, nastavte jeho <xref:System.Windows.Forms.BorderStyle> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0ede5-111">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="0ede5-112">Existují tři možnosti: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle> <xref:System.Windows.Forms.BorderStyle.None>a.</span><span class="sxs-lookup"><span data-stu-id="0ede5-112">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ede5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ede5-113">See also</span></span>

- [<span data-ttu-id="0ede5-114">Ovládací prvek Panel</span><span class="sxs-lookup"><span data-stu-id="0ede5-114">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="0ede5-115">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="0ede5-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="0ede5-116">Postupy: Nastavení pozadí panelu</span><span class="sxs-lookup"><span data-stu-id="0ede5-116">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
