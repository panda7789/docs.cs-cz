---
title: 'Postupy: Vytvoření jednoduše připojeného ovládacího prvku na Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538815"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="c55b0-102">Postupy: Vytvoření jednoduše připojeného ovládacího prvku na Windows Form</span><span class="sxs-lookup"><span data-stu-id="c55b0-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>
<span data-ttu-id="c55b0-103">S *jednoduchá vazba*, jeden datový prvek, jako je například hodnota sloupce z tabulky datovou sadu, může zobrazení v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c55b0-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="c55b0-104">Vám může jednoduché bind libovolné vlastnosti ovládacího prvku na hodnotu data.</span><span class="sxs-lookup"><span data-stu-id="c55b0-104">You can simple-bind any property of a control to a data value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c55b0-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c55b0-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c55b0-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c55b0-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c55b0-107">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c55b0-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-simple-bind-a-control"></a><span data-ttu-id="c55b0-108">Na jednoduchý vytvořte vazbu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c55b0-108">To simple-bind a control</span></span>  
  
1.  <span data-ttu-id="c55b0-109">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="c55b0-109">Connect to a data source.</span></span> <span data-ttu-id="c55b0-110">Další informace najdete v tématu [připojení ke zdroji dat](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="c55b0-110">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="c55b0-111">Ve formuláři, vyberte ovládací prvek a zobrazit **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c55b0-111">In the form, select the control and display the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="c55b0-112">Rozbalte **(datové vazby)** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c55b0-112">Expand the **(DataBindings)** property.</span></span>  
  
     <span data-ttu-id="c55b0-113">Vlastnosti nejčastěji vázaný se zobrazí pod **(datové vazby)** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c55b0-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="c55b0-114">Například v většina ovládacích prvků **Text** vlastnost je nejčastěji vázána.</span><span class="sxs-lookup"><span data-stu-id="c55b0-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>  
  
4.  <span data-ttu-id="c55b0-115">Pokud vlastnost, kterou chcete vazby není jednou z nejčastěji vázané vlastnosti, klikněte na **třemi tečkami** tlačítko (![VisualStudioEllipsesButton snímek](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) v **(rozšířené)** políčka se zobrazí **formátování a rozšířené vazby** dialogové okno s úplný seznam vlastností pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c55b0-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>  
  
5.  <span data-ttu-id="c55b0-116">Vyberte vlastnost, kterou chcete vytvořit vazbu a klikněte na šipku rozevíracího seznamu v části **vazby**.</span><span class="sxs-lookup"><span data-stu-id="c55b0-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>  
  
     <span data-ttu-id="c55b0-117">Zobrazí se seznam dostupných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="c55b0-117">A list of available data sources is displayed.</span></span>  
  
6.  <span data-ttu-id="c55b0-118">Rozbalení zdroje dat, které chcete vytvořit vazbu, dokud nebude nalezen jeden datový prvek, který má být.</span><span class="sxs-lookup"><span data-stu-id="c55b0-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="c55b0-119">Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky k zobrazení názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="c55b0-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
7.  <span data-ttu-id="c55b0-120">Klikněte na název elementu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="c55b0-120">Click the name of an element to bind to.</span></span>  
  
8.  <span data-ttu-id="c55b0-121">Pokud jste pracovali **formátování a rozšířené vazby** dialogové okno, klikněte na tlačítko **OK** se vrátíte do **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c55b0-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>  
  
9. <span data-ttu-id="c55b0-122">Pokud chcete vytvořit vazbu další vlastnosti ovládacího prvku, opakujte kroky 3 až 7.</span><span class="sxs-lookup"><span data-stu-id="c55b0-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c55b0-123">Protože ovládací prvky vázané na jednoduchý zobrazit pouze jeden datový prvek, je velmi typické zahrnout logiku navigace ve formuláři Windows s ovládací prvky vázané na jednoduché.</span><span class="sxs-lookup"><span data-stu-id="c55b0-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55b0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c55b0-124">See Also</span></span>  
 <xref:System.Windows.Forms.Binding>  
 [<span data-ttu-id="c55b0-125">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="c55b0-125">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="c55b0-126">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c55b0-126">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
