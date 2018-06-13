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
ms.openlocfilehash: a78286be8ef64212d945b3cb11a2963d5a1b2e79
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535344"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a><span data-ttu-id="2762c-102">Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2762c-102">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>
<span data-ttu-id="2762c-103">Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> řízení může mít rozsah sousedících řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="2762c-103">Controls in a <xref:System.Windows.Forms.TableLayoutPanel> control can span adjacent rows and columns.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2762c-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="2762c-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2762c-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2762c-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2762c-106">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="2762c-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-span-columns-and-rows"></a><span data-ttu-id="2762c-107">Zabraných sloupců a řádků</span><span class="sxs-lookup"><span data-stu-id="2762c-107">To span columns and rows</span></span>  
  
1.  <span data-ttu-id="2762c-108">Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="2762c-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="2762c-109">Přetažení <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do levého horního buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="2762c-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
3.  <span data-ttu-id="2762c-110">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="2762c-110">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **2**.</span></span> <span data-ttu-id="2762c-111">Všimněte si, že <xref:System.Windows.Forms.Button> řízení zahrnuje prvním a druhém sloupci.</span><span class="sxs-lookup"><span data-stu-id="2762c-111">Note that the <xref:System.Windows.Forms.Button> control spans the first and second columns.</span></span>  
  
4.  <span data-ttu-id="2762c-112">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **RowSpan** vlastnost **2**.</span><span class="sxs-lookup"><span data-stu-id="2762c-112">Set the <xref:System.Windows.Forms.Button> control's **RowSpan** property to **2**.</span></span> <span data-ttu-id="2762c-113">Všimněte si, že <xref:System.Windows.Forms.Button> řízení zahrnuje prvním a druhém řádku.</span><span class="sxs-lookup"><span data-stu-id="2762c-113">Note that the <xref:System.Windows.Forms.Button> control spans the first and second rows.</span></span>  
  
5.  <span data-ttu-id="2762c-114">Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **1**.</span><span class="sxs-lookup"><span data-stu-id="2762c-114">Set the <xref:System.Windows.Forms.Button> control's **ColumnSpan** property to **1**.</span></span> <span data-ttu-id="2762c-115">Všimněte si, že <xref:System.Windows.Forms.Button> řízení přesune do prvního sloupce a zahrnuje prvním a druhém řádku.</span><span class="sxs-lookup"><span data-stu-id="2762c-115">Note that the <xref:System.Windows.Forms.Button> control moves into the first column and spans the first and second rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2762c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2762c-116">See Also</span></span>  
 [<span data-ttu-id="2762c-117">Ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2762c-117">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
