---
title: "TableLayoutPanel – přehled ovládacího prvku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 614887524a49e1163b3049111895166995fdace4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="f3ed9-102">TableLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f3ed9-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="f3ed9-103"><xref:System.Windows.Forms.TableLayoutPanel> Řízení uspořádá jeho obsah v mřížce.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="f3ed9-104">Protože je prováděna rozložení i v době návrhu a běh, ho můžete změnit dynamicky jako změny prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="f3ed9-105">To umožňuje ovládacích prvků v panelu se úměrně změnit velikost, tak může reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka změna z důvodu lokalizace.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="f3ed9-106">Libovolný ovládací prvek Windows Forms může být podřízená <xref:System.Windows.Forms.TableLayoutPanel> řízení, včetně ostatní instance <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="f3ed9-107">Umožňuje vytvořit sofistikované rozložení, které se změny v době běhu přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="f3ed9-108"><xref:System.Windows.Forms.TableLayoutPanel> Řízení můžete rozšířit, aby odpovídala nové ovládací prvky, když budou přidány, v závislosti na hodnotě <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, a <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="f3ed9-109">Nastavení buď <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> nebo <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> vlastnost na hodnotu 0 určuje, že <xref:System.Windows.Forms.TableLayoutPanel> bude nevázaných v odpovídající směru.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="f3ed9-110">Můžete taky řídit směr rozšíření (vodorovné nebo svislé), po <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="f3ed9-111">Ve výchozím nastavení <xref:System.Windows.Forms.TableLayoutPanel> řízení rozšíří dolů přidáním řádků.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="f3ed9-112">Pokud chcete řádky a sloupce, které se chovají jinak než výchozí chování, můžete řídit vlastnosti řádků a sloupců pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="f3ed9-113">Vlastnosti řádky nebo sloupce můžete nastavit samostatně.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="f3ed9-114"><xref:System.Windows.Forms.TableLayoutPanel> Řízení přidá následující vlastnosti do jeho podřízených ovládacích prvků: `Cell`, `Column`, `Row`, `ColumnSpan`, a `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="f3ed9-115">Sloučením buněk v <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek pro nastavení `ColumnSpan` nebo `RowSpan` vlastností podřízeného prvku.</span><span class="sxs-lookup"><span data-stu-id="f3ed9-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1.  <span data-ttu-id="f3ed9-116">[Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f3ed9-116">[How to: Align and Stretch a Control in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))</span></span>  
  
2.  <span data-ttu-id="f3ed9-117">[Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f3ed9-117">[How to: Span Rows and Columns in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))</span></span>  
  
3.  <span data-ttu-id="f3ed9-118">[Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f3ed9-118">[How to: Edit Columns and Rows in a TableLayoutPanel Control](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))</span></span>  
  
4.  <span data-ttu-id="f3ed9-119">[Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="f3ed9-119">[Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ed9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3ed9-120">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [<span data-ttu-id="f3ed9-121">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="f3ed9-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [<span data-ttu-id="f3ed9-122">Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="f3ed9-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [<span data-ttu-id="f3ed9-123">Doporučené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f3ed9-123">Best Practices for the TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
