---
title: TableLayoutPanel – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: 65daba0ce1a6f1c37fb257c1029396577821aad9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295364"
---
# <a name="tablelayoutpanel-control-overview"></a><span data-ttu-id="7178b-102">TableLayoutPanel – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="7178b-102">TableLayoutPanel Control Overview</span></span>
<span data-ttu-id="7178b-103"><xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek uspořádá její obsah do mřížky.</span><span class="sxs-lookup"><span data-stu-id="7178b-103">The <xref:System.Windows.Forms.TableLayoutPanel> control arranges its contents in a grid.</span></span> <span data-ttu-id="7178b-104">Protože je prováděna rozložení i v době návrhu a běhu, můžete změnit dynamicky se změnami prostředí aplikace.</span><span class="sxs-lookup"><span data-stu-id="7178b-104">Because the layout is performed both at design time and run time, it can change dynamically as the application environment changes.</span></span> <span data-ttu-id="7178b-105">To umožňuje ovládací prvky v panelu proporcionálně velikost, tak můžou reagovat na změny, jako je například změna velikosti nadřazeného ovládacího prvku nebo text délka mění kvůli lokalizace.</span><span class="sxs-lookup"><span data-stu-id="7178b-105">This gives the controls in the panel the ability to proportionally resize, so they can respond to changes such as the parent control resizing or text length changing due to localization.</span></span>  
  
 <span data-ttu-id="7178b-106">Libovolný ovládací prvek Windows Forms může být podřízený <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek, včetně dalších instancí <xref:System.Windows.Forms.TableLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="7178b-106">Any Windows Forms control can be a child of the <xref:System.Windows.Forms.TableLayoutPanel> control, including other instances of <xref:System.Windows.Forms.TableLayoutPanel>.</span></span> <span data-ttu-id="7178b-107">To umožňuje vytvořit sofistikované rozložení, které přizpůsoboval změnám v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7178b-107">This allows you to construct sophisticated layouts that adapt to changes at run time.</span></span>  
  
 <span data-ttu-id="7178b-108"><xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku můžete rozšířit tak, aby vyhovovaly nových ovládacích prvků, když se přidají, závisí na hodnotě <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, a <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7178b-108">The <xref:System.Windows.Forms.TableLayoutPanel> control can expand to accommodate new controls when they are added, depending on the value of the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>, and <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> properties.</span></span> <span data-ttu-id="7178b-109">Nastavení buď <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> nebo <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> vlastnost na hodnotu 0 určuje, že <xref:System.Windows.Forms.TableLayoutPanel> bude nevázaných ve směru odpovídající.</span><span class="sxs-lookup"><span data-stu-id="7178b-109">Setting either the <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> or <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> property to a value of 0 specifies that the <xref:System.Windows.Forms.TableLayoutPanel> will be unbound in the corresponding direction.</span></span>  
  
 <span data-ttu-id="7178b-110">Můžete také řídit směr rozbalení (horizontal nebo vertical) po <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek je plná podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="7178b-110">You can also control the direction of expansion (horizontal or vertical) after the <xref:System.Windows.Forms.TableLayoutPanel> control is full of child controls.</span></span> <span data-ttu-id="7178b-111">Ve výchozím nastavení <xref:System.Windows.Forms.TableLayoutPanel> rozbalí přidáním řádků ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7178b-111">By default, the <xref:System.Windows.Forms.TableLayoutPanel> control expands downward by adding rows.</span></span>  
  
 <span data-ttu-id="7178b-112">Pokud chcete řádky a sloupce, které se chovají odlišně od výchozí chování, můžete řídit vlastnosti řádků a sloupců pomocí <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> a <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7178b-112">If you want rows and columns that behave differently from the default behavior, you can control the properties of rows and columns by using the <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> and <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> properties.</span></span> <span data-ttu-id="7178b-113">Můžete nastavit vlastnosti řádky nebo sloupce samostatně.</span><span class="sxs-lookup"><span data-stu-id="7178b-113">You can set the properties of rows or columns individually.</span></span>  
  
 <span data-ttu-id="7178b-114"><xref:System.Windows.Forms.TableLayoutPanel> Ovládacího prvku přidá následující vlastnosti do jeho podřízených ovládacích prvků: `Cell`, `Column`, `Row`, `ColumnSpan`, a `RowSpan`.</span><span class="sxs-lookup"><span data-stu-id="7178b-114">The <xref:System.Windows.Forms.TableLayoutPanel> control adds the following properties to its child controls: `Cell`, `Column`, `Row`, `ColumnSpan`, and `RowSpan`.</span></span>  
  
 <span data-ttu-id="7178b-115">Můžete sloučit buňky v <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku tak, že nastavíte `ColumnSpan` nebo `RowSpan` vlastnosti na podřízený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7178b-115">You can merge cells in the <xref:System.Windows.Forms.TableLayoutPanel> control by setting the `ColumnSpan` or `RowSpan` properties on a child control.</span></span>  
  
1. [<span data-ttu-id="7178b-116">Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7178b-116">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [<span data-ttu-id="7178b-117">Postupy: Rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7178b-117">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3. [<span data-ttu-id="7178b-118">Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7178b-118">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4. [<span data-ttu-id="7178b-119">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7178b-119">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
  
## <a name="see-also"></a><span data-ttu-id="7178b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7178b-120">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutSettings>
- [<span data-ttu-id="7178b-121">Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci</span><span class="sxs-lookup"><span data-stu-id="7178b-121">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="7178b-122">Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat</span><span class="sxs-lookup"><span data-stu-id="7178b-122">How to: Create a Resizable Windows Form for Data Entry</span></span>](how-to-create-a-resizable-windows-form-for-data-entry.md)
- [<span data-ttu-id="7178b-123">Doporučené postupy pro ovládací prvek TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7178b-123">Best Practices for the TableLayoutPanel Control</span></span>](best-practices-for-the-tablelayoutpanel-control.md)
