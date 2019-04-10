---
title: 'Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě sady'
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 857e61bc89e072aebcf34793d7e8504ece3318c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307251"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="3ae37-102">Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě sady</span><span class="sxs-lookup"><span data-stu-id="3ae37-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="3ae37-103">Windows Forms <xref:System.Windows.Forms.RadioButton> ovládací prvky jsou navrženy a poskytuje tak uživatelům možnost volby mezi dvěma nebo více nastavení, z nichž je možné přiřadit pouze jeden procedura nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="3ae37-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="3ae37-104">Například skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky se může zobrazit celou řadu prostředníci balíčku pro objednávku, ale pouze jeden z dopravce se použije.</span><span class="sxs-lookup"><span data-stu-id="3ae37-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="3ae37-105">Proto pouze jeden <xref:System.Windows.Forms.RadioButton> najednou lze vybrat, i když je součástí skupiny funkční.</span><span class="sxs-lookup"><span data-stu-id="3ae37-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="3ae37-106">Přepínací tlačítka seskupit, jako je vykreslování uvnitř kontejneru <xref:System.Windows.Forms.Panel> ovládací prvek, <xref:System.Windows.Forms.GroupBox> ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="3ae37-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="3ae37-107">Všechny přepínače, které jsou přidány přímo do jedné skupiny formuláře stát.</span><span class="sxs-lookup"><span data-stu-id="3ae37-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="3ae37-108">Chcete-li přidat samostatné skupiny, je nutné je umístit uvnitř panely nebo skupinové rámečky.</span><span class="sxs-lookup"><span data-stu-id="3ae37-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="3ae37-109">Další informace o panely nebo skupinové rámečky najdete v tématu [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md) nebo [groupbox – Přehled ovládacího prvku](groupbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3ae37-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="3ae37-110">Pro ovládací prvky RadioButton skupiny jako sada funkce nezávisle na jiných sadách</span><span class="sxs-lookup"><span data-stu-id="3ae37-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="3ae37-111">Přetáhněte <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> ovládacího prvku **Windows Forms** kartě **nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="3ae37-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="3ae37-112">Nakreslit <xref:System.Windows.Forms.RadioButton> ovládací prvky na <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3ae37-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae37-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ae37-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="3ae37-114">Přehled ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="3ae37-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="3ae37-115">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="3ae37-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="3ae37-116">Přehled ovládacího prvku GroupBox</span><span class="sxs-lookup"><span data-stu-id="3ae37-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="3ae37-117">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="3ae37-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="3ae37-118">Ovládací prvek RadioButton</span><span class="sxs-lookup"><span data-stu-id="3ae37-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
