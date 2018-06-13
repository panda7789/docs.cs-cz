---
title: 'Postupy: Zobrazení bočně zarovnaných karet pomocí TabControl'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: e145547ba4c8648a765e9507b7f35e50cb15fd82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532458"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="6ecfe-102">Postupy: Zobrazení bočně zarovnaných karet pomocí TabControl</span><span class="sxs-lookup"><span data-stu-id="6ecfe-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="6ecfe-103"><xref:System.Windows.Forms.TabControl.Alignment%2A> Vlastnost <xref:System.Windows.Forms.TabControl> podporuje zobrazení karet svisle (společně levý nebo pravý okraj ovládacího prvku), naproti tomu vodorovně (přes horní nebo dolní části ovládacího prvku).</span><span class="sxs-lookup"><span data-stu-id="6ecfe-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="6ecfe-104">Ve výchozím nastavení, tento svislé zobrazení výsledků v nízký uživatelské prostředí, protože <xref:System.Windows.Forms.TabPage.Text%2A> vlastnost <xref:System.Windows.Forms.TabPage> objekt nejsou zobrazeny na kartě, pokud jsou povolené vizuální styly.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="6ecfe-105">Je také přímý způsob, jak řídit směru textu v rámci kartě. Můžete použít vlastníka kreslení v <xref:System.Windows.Forms.TabControl> ke zlepšení toto prostředí.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="6ecfe-106">Následující postup ukazuje, jak k vykreslení vpravo bočně zarovnaných karet s textem karta službou zleva doprava, a použijte funkci "kreslení vlastníka".</span><span class="sxs-lookup"><span data-stu-id="6ecfe-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="6ecfe-107">Chcete-li zobrazit práva bočně zarovnaných karet</span><span class="sxs-lookup"><span data-stu-id="6ecfe-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="6ecfe-108">Přidat <xref:System.Windows.Forms.TabControl> do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="6ecfe-109">Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="6ecfe-110">Nastavte <xref:System.Windows.Forms.TabControl.SizeMode%2A> vlastnost <xref:System.Windows.Forms.TabSizeMode.Fixed>tak, aby všechny karty jsou stejné šířky.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="6ecfe-111">Nastavte <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost upřednostňovanou pevnou velikost karty.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="6ecfe-112">Mějte na paměti, že <xref:System.Windows.Forms.TabControl.ItemSize%2A> vlastnost chová, jako by byly na karty nahoře, i když jsou zarovnaný doprava.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="6ecfe-113">Výsledkem je, aby bylo možné širší karty, musíte změnit <xref:System.Drawing.Size.Height%2A> vlastnost, a aby bylo možné je vyšší, musíte změnit <xref:System.Drawing.Size.Width%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="6ecfe-114">Nejlepších výsledků s následujícím příkladu kódu nastavit <xref:System.Drawing.Size.Width%2A> z karet na 25 a <xref:System.Drawing.Size.Height%2A> do 100.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="6ecfe-115">Nastavte <xref:System.Windows.Forms.TabControl.DrawMode%2A> vlastnost <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="6ecfe-116">Definování obslužné rutiny pro <xref:System.Windows.Forms.TabControl.DrawItem> události <xref:System.Windows.Forms.TabControl> , vykreslí textu zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="6ecfe-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6ecfe-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ecfe-117">See Also</span></span>  
 [<span data-ttu-id="6ecfe-118">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="6ecfe-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
