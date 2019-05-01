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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012968"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="1c12f-102">Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1c12f-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="1c12f-103">Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek může mít rozsah sousední řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="1c12f-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c12f-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="1c12f-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1c12f-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="1c12f-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1c12f-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1c12f-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="1c12f-107">Rozložit sloupců a řádků</span><span class="sxs-lookup"><span data-stu-id="1c12f-107">To span columns and rows</span></span>  
  
1. <span data-ttu-id="1c12f-108">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="1c12f-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2. <span data-ttu-id="1c12f-109">Přetáhněte <xref:System.Windows.Forms.Button> ovládacího prvku **nástrojů** do buňky levého horního <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1c12f-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3. <span data-ttu-id="1c12f-110">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="1c12f-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="1c12f-111">Všimněte si, že <xref:System.Windows.Forms.Button> ovládací prvek zahrnuje prvního a druhého sloupce.</span><span class="sxs-lookup"><span data-stu-id="1c12f-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4. <span data-ttu-id="1c12f-112">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **RowSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="1c12f-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="1c12f-113">Všimněte si, <xref:System.Windows.Forms.Button> první a druhý řádek obsahuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1c12f-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5. <span data-ttu-id="1c12f-114">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **1**.</span><span class="sxs-lookup"><span data-stu-id="1c12f-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="1c12f-115">Všimněte si, <xref:System.Windows.Forms.Button> ovládacího prvku přesune na první sloupec a zahrnuje první a druhý řádek.</span><span class="sxs-lookup"><span data-stu-id="1c12f-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c12f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c12f-116">See also</span></span>

- [<span data-ttu-id="1c12f-117">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1c12f-117">TableLayoutPanel Control</span></span>](tablelayoutpanel-control-windows-forms.md)
