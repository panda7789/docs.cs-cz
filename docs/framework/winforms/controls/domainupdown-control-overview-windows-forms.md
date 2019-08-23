---
title: DomainUpDown – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
ms.openlocfilehash: 6fda542204e2b41dd1d729d2b940c6f38a5812ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965304"
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="6dd17-102">DomainUpDown – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6dd17-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="6dd17-103">Model Windows Forms <xref:System.Windows.Forms.DomainUpDown> ovládací prvek je v podstatě kombinací textového pole a dvojice tlačítek pro pohyb nahoru nebo dolů v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6dd17-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="6dd17-104">Ovládací prvek zobrazí a nastaví textový řetězec ze seznamu možností.</span><span class="sxs-lookup"><span data-stu-id="6dd17-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="6dd17-105">Uživatel může vybrat řetězec kliknutím na tlačítko nahoru a dolů pro pohyb v seznamu stisknutím kláves se šipkami nahoru a dolů nebo zadáním řetězce, který odpovídá položce v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6dd17-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="6dd17-106">Jedním z možných použití tohoto ovládacího prvku je výběr položek z abecedně seřazeného seznamu názvů.</span><span class="sxs-lookup"><span data-stu-id="6dd17-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dd17-107">Chcete-li seznam seřadit, nastavte <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> vlastnost na `true`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6dd17-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="6dd17-108">Funkce tohoto ovládacího prvku je velmi podobná poli seznamu nebo pole se seznamem, ale zabírá velmi málo místa.</span><span class="sxs-lookup"><span data-stu-id="6dd17-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="6dd17-109">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="6dd17-109">Key Properties</span></span>  
 <span data-ttu-id="6dd17-110">Klíčové vlastnosti ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>a <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="6dd17-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="6dd17-111"><xref:System.Windows.Forms.DomainUpDown.Items%2A> Vlastnost obsahuje seznam objektů, jejichž textové hodnoty jsou zobrazeny v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="6dd17-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="6dd17-112">Pokud <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> je nastaveno na `false`, ovládací prvek automaticky dokončí text, který uživatel zadá a odpovídá hodnotě v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6dd17-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="6dd17-113">Pokud <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> je nastaveno na `true`, posun za poslední položkou přejde na první položku v seznamu a naopak.</span><span class="sxs-lookup"><span data-stu-id="6dd17-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="6dd17-114">Klíčové metody ovládacího prvku jsou <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> a. <xref:System.Windows.Forms.DomainUpDown.DownButton%2A></span><span class="sxs-lookup"><span data-stu-id="6dd17-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="6dd17-115">Tento ovládací prvek zobrazí pouze textové řetězce.</span><span class="sxs-lookup"><span data-stu-id="6dd17-115">This control displays only text strings.</span></span> <span data-ttu-id="6dd17-116">Pokud chcete ovládací prvek, který zobrazuje číselné hodnoty, použijte <xref:System.Windows.Forms.NumericUpDown> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6dd17-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="6dd17-117">Další informace naleznete v tématu [Přehled ovládacího prvku NumericUpDown](numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6dd17-117">For more information, see [NumericUpDown Control Overview](numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd17-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dd17-118">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- [<span data-ttu-id="6dd17-119">Ovládací prvek DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="6dd17-119">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
