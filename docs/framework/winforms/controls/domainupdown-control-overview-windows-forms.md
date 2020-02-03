---
title: Přehled ovládacího prvku DomainUpDown
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 86703a96d4845414d043161e0efa67bfde9278db
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745856"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="5f980-102">DomainUpDown – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5f980-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="5f980-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.DomainUpDown> je v podstatě kombinací textového pole a dvojice tlačítek pro pohyb nahoru nebo dolů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5f980-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="5f980-104">Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu možností.</span><span class="sxs-lookup"><span data-stu-id="5f980-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="5f980-105">Uživatel může vybrat řetězec kliknutím na tlačítko nahoru a dolů pro pohyb v seznamu stisknutím kláves se šipkami nahoru a dolů nebo zadáním řetězce, který odpovídá položce v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5f980-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="5f980-106">Jedním z možných použití tohoto ovládacího prvku je výběr položek z abecedně seřazeného seznamu názvů.</span><span class="sxs-lookup"><span data-stu-id="5f980-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f980-107">Chcete-li seznam seřadit, nastavte vlastnost <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="5f980-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="5f980-108">Funkce tohoto ovládacího prvku je velmi podobná poli seznamu nebo pole se seznamem, ale zabírá velmi málo místa.</span><span class="sxs-lookup"><span data-stu-id="5f980-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="5f980-109">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5f980-109">Key Properties</span></span>  
 <span data-ttu-id="5f980-110">Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f980-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="5f980-111">Vlastnost <xref:System.Windows.Forms.DomainUpDown.Items%2A> obsahuje seznam objektů, jejichž textové hodnoty jsou zobrazeny v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="5f980-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="5f980-112">Pokud je <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> nastaveno na `false`, ovládací prvek automaticky dokončí text, který uživatel zadá a odpovídá hodnotě v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5f980-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="5f980-113">Pokud je <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> nastaveno na `true`, posun za poslední položkou přejde na první položku v seznamu a naopak.</span><span class="sxs-lookup"><span data-stu-id="5f980-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="5f980-114">Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="5f980-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="5f980-115">Tento ovládací prvek zobrazí pouze textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="5f980-115">This control displays only text strings.</span></span> <span data-ttu-id="5f980-116">Pokud chcete ovládací prvek, který zobrazuje číselné hodnoty, použijte ovládací prvek <xref:System.Windows.Forms.NumericUpDown>.</span><span class="sxs-lookup"><span data-stu-id="5f980-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="5f980-117">Další informace naleznete v tématu [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5f980-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f980-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f980-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="5f980-119">Ovládací prvek DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="5f980-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
