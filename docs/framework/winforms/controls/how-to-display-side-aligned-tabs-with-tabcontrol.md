---
title: 'Postupy: Zobrazení bočně zarovnaných karet pomocí ovládacího prvku TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: d98c5906d99dff9371f8290e7dbc9c9011cd0c29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338784"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="ff24d-102">Postupy: Zobrazení bočně zarovnaných karet pomocí ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="ff24d-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="ff24d-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Vlastnost <xref:System.Windows.Forms.TabControl> podporuje zobrazení tabulek svisle (podél levého nebo pravého okraje ovládacího prvku) nikoli vodorovně (v horní nebo dolní okraj ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="ff24d-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="ff24d-104">Ve výchozím nastavení, svislé zobrazení má za následek nízký uživatelské prostředí, protože <xref:System.Windows.Forms.TabPage.Text%2A> vlastnost <xref:System.Windows.Forms.TabPage> objekt se nezobrazuje na kartě Pokud jsou vizuální styly povoleny.</span><span class="sxs-lookup"><span data-stu-id="ff24d-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="ff24d-105">Neexistuje žádný přímý způsob, jak řídit směr textu v kartě. Můžete použít vlastníka nakreslit <xref:System.Windows.Forms.TabControl> na zdokonalování tohoto prostředí.</span><span class="sxs-lookup"><span data-stu-id="ff24d-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="ff24d-106">Následující postup ukazuje, jak lze vykreslit vpravo bočně zarovnaných karet s textem karty systémem zleva doprava, pomocí funkce "owner draw".</span><span class="sxs-lookup"><span data-stu-id="ff24d-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="ff24d-107">Chcete-li zobrazit vpravo bočně zarovnaných karet</span><span class="sxs-lookup"><span data-stu-id="ff24d-107">To display right-aligned tabs</span></span>  
  
1. <span data-ttu-id="ff24d-108">Přidat <xref:System.Windows.Forms.TabControl> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="ff24d-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2. <span data-ttu-id="ff24d-109">Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="ff24d-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3. <span data-ttu-id="ff24d-110">Nastavte <xref:System.Windows.Forms.TabControl.SizeMode%2A> vlastnost <xref:System.Windows.Forms.TabSizeMode.Fixed>, tak, že jsou všechny karty mají stejnou šířku.</span><span class="sxs-lookup"><span data-stu-id="ff24d-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4. <span data-ttu-id="ff24d-111">Nastavte <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost upřednostňovanou pevnou velikost karet.</span><span class="sxs-lookup"><span data-stu-id="ff24d-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="ff24d-112">Mějte na paměti, která <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost chová, jako by byly karty v horní části, i když jsou zarovnaná vpravo.</span><span class="sxs-lookup"><span data-stu-id="ff24d-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="ff24d-113">Kvůli tomu, aby bylo možné širší karty, musíte změnit <xref:System.Drawing.Size.Height%2A> vlastnost, a aby bylo možné je vyšší, musíte změnit <xref:System.Drawing.Size.Width%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ff24d-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="ff24d-114">Pro nejlepší výsledky s následující příklad kódu, nastavte <xref:System.Drawing.Size.Width%2A> karet na 25 a <xref:System.Drawing.Size.Height%2A> do 100.</span><span class="sxs-lookup"><span data-stu-id="ff24d-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5. <span data-ttu-id="ff24d-115">Nastavte <xref:System.Windows.Forms.TabControl.DrawMode%2A> vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="ff24d-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6. <span data-ttu-id="ff24d-116">Definování obslužné rutiny pro <xref:System.Windows.Forms.TabControl.DrawItem> událost <xref:System.Windows.Forms.TabControl> , která generuje text zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="ff24d-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ff24d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff24d-117">See also</span></span>

- [<span data-ttu-id="ff24d-118">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="ff24d-118">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
