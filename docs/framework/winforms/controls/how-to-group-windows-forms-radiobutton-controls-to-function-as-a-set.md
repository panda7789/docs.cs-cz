---
title: "Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c92048374941f735568bcd758ed475eba78b81e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="52707-102">Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny</span><span class="sxs-lookup"><span data-stu-id="52707-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="52707-103">Windows Forms <xref:System.Windows.Forms.RadioButton> ovládací prvky jsou navrženy umožnit uživateli vybrat mezi dva nebo více nastavení, ve kterých lze přiřadit pouze jeden postup nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="52707-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="52707-104">Například skupina <xref:System.Windows.Forms.RadioButton> ovládací prvky se může zobrazovat vybrat balíček prostředníci pro pořadí, ale pouze jedna prostředníci se použije.</span><span class="sxs-lookup"><span data-stu-id="52707-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="52707-105">Proto pouze jeden <xref:System.Windows.Forms.RadioButton> najednou lze vybrat, i když je součástí skupiny funkčnosti.</span><span class="sxs-lookup"><span data-stu-id="52707-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="52707-106">Skupina přepínacích tlačítek podle například výkresu uvnitř kontejneru <xref:System.Windows.Forms.Panel> řízení, <xref:System.Windows.Forms.GroupBox> ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="52707-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="52707-107">Všech přepínačů přidané přímo do formuláře stane jedné skupiny.</span><span class="sxs-lookup"><span data-stu-id="52707-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="52707-108">Chcete-li přidat samostatné skupiny, je nutné umístit uvnitř panelů nebo skupinové rámečky.</span><span class="sxs-lookup"><span data-stu-id="52707-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="52707-109">Další informace o panelů nebo skupinové rámečky najdete v tématu [Přehled ovládacího prvku Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) nebo [groupbox – Přehled ovládacího prvku](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="52707-109">For more information about panels or group boxes, see [Panel Control Overview](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md) or [GroupBox Control Overview](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="52707-110">Do skupiny RadioButton – ovládací prvky jako sada funkce nezávisle na jiné sady</span><span class="sxs-lookup"><span data-stu-id="52707-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1.  <span data-ttu-id="52707-111">Přetáhněte <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> řídit z **Windows Forms** na kartě **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="52707-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="52707-112">Kreslení <xref:System.Windows.Forms.RadioButton> ovládací prvky na <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="52707-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52707-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="52707-113">See Also</span></span>  
 <xref:System.Windows.Forms.RadioButton>  
 [<span data-ttu-id="52707-114">Přehled ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="52707-114">RadioButton Control Overview</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-overview-windows-forms.md)  
 [<span data-ttu-id="52707-115">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="52707-115">Panel Control Overview</span></span>](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [<span data-ttu-id="52707-116">Přehled ovládacího prvku GroupBox</span><span class="sxs-lookup"><span data-stu-id="52707-116">GroupBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="52707-117">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="52707-117">CheckBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="52707-118">Ovládací prvek RadioButton</span><span class="sxs-lookup"><span data-stu-id="52707-118">RadioButton Control</span></span>](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)
