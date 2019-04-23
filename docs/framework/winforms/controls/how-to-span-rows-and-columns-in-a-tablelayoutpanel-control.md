---
title: 'Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: 02db78b07930676235e55e535fb24f6ff618d823
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59339018"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="8cfca-102">Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8cfca-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="8cfca-103">Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek může mít rozsah sousední řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="8cfca-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cfca-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="8cfca-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="8cfca-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="8cfca-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="8cfca-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="8cfca-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="8cfca-107">Rozložit sloupců a řádků</span><span class="sxs-lookup"><span data-stu-id="8cfca-107">To span columns and rows</span></span>  
  
1. <span data-ttu-id="8cfca-108">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="8cfca-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="8cfca-109">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8cfca-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3. <span data-ttu-id="8cfca-110">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="8cfca-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="8cfca-111">Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek zahrnuje prvního a druhého sloupce.</span><span class="sxs-lookup"><span data-stu-id="8cfca-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4. <span data-ttu-id="8cfca-112">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **RowSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="8cfca-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="8cfca-113">Všimněte si, <xref:System.Windows.Forms.Button> první a druhý řádek obsahuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8cfca-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5. <span data-ttu-id="8cfca-114">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **1**.</span><span class="sxs-lookup"><span data-stu-id="8cfca-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="8cfca-115">Všimněte si, <xref:System.Windows.Forms.Button> ovládacího prvku přesune na první sloupec a zahrnuje první a druhý řádek.</span><span class="sxs-lookup"><span data-stu-id="8cfca-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cfca-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cfca-116">See also</span></span>

- [<span data-ttu-id="8cfca-117">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="8cfca-117">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
