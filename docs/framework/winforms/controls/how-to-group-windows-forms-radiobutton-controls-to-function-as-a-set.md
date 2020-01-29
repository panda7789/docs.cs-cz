---
title: Seskupit ovládací prvky RadioButton pro funkci jako sadu
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: c4b37c84bf0f93837b91c743c7681d39fd83a659
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732948"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="0eb2b-102">Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny</span><span class="sxs-lookup"><span data-stu-id="0eb2b-102">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="0eb2b-103">Ovládací prvky model Windows Forms <xref:System.Windows.Forms.RadioButton> jsou navržené tak, aby uživatelům poskytovaly možnost volby mezi dvěma nebo více nastaveními, z nichž je možné přiřadit jenom jednu proceduru nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-103">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="0eb2b-104">Například skupina ovládacích prvků <xref:System.Windows.Forms.RadioButton> může zobrazit výběr nosičů balíčků pro objednávku, ale budou použity pouze jeden z dopravců.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-104">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="0eb2b-105">Proto lze vybrat pouze jeden <xref:System.Windows.Forms.RadioButton> v jednom okamžiku, i když je součástí funkční skupiny.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-105">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="0eb2b-106">Přepínače můžete seskupovat tak, že je vykreslíte do kontejneru, jako je <xref:System.Windows.Forms.Panel> ovládací prvek, ovládací prvek <xref:System.Windows.Forms.GroupBox> nebo formulář.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-106">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="0eb2b-107">Všechna přepínací tlačítka, která jsou přidána přímo do formuláře, se stanou jednou skupinou.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-107">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="0eb2b-108">Chcete-li přidat samostatné skupiny, je nutné je umístit do panelů nebo skupinových polí.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-108">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="0eb2b-109">Další informace o panelech nebo skupinových polích naleznete v tématu [Přehled ovládacího prvku panel](panel-control-overview-windows-forms.md) nebo [Přehled ovládacího prvku skupinový](groupbox-control-overview-windows-forms.md)odkaz.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-109">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="0eb2b-110">Seskupení ovládacích prvků RadioButton jako sady funkcí nezávisle na jiných sadách</span><span class="sxs-lookup"><span data-stu-id="0eb2b-110">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="0eb2b-111">Přetáhněte ovládací prvek <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> z karty **model Windows Forms** na **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-111">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="0eb2b-112">Nakreslete ovládací prvky <xref:System.Windows.Forms.RadioButton> ovládacího prvku <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="0eb2b-112">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb2b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0eb2b-113">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="0eb2b-114">Přehled ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="0eb2b-114">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="0eb2b-115">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="0eb2b-115">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="0eb2b-116">Přehled ovládacího prvku GroupBox</span><span class="sxs-lookup"><span data-stu-id="0eb2b-116">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="0eb2b-117">Přehled ovládacího prvku CheckBox</span><span class="sxs-lookup"><span data-stu-id="0eb2b-117">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="0eb2b-118">Ovládací prvek RadioButton</span><span class="sxs-lookup"><span data-stu-id="0eb2b-118">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
