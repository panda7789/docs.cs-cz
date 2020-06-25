---
title: Seskupit ovládací prvky RadioButton pro funkci jako sadu
description: Naučte se, jak seskupit model Windows Forms ovládací prvky RadioButton, aby fungovaly nezávisle na jiných sadách.
ms.date: 03/30/2017
helpviewer_keywords:
- radio buttons [Windows Forms], grouping
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
- RadioButton control [Windows Forms], grouping
ms.assetid: 58f8fe34-50b7-49d8-a2be-c271be3c6b32
ms.openlocfilehash: 9f6795330922e739cca1f2b5c11bb2ec68bb4e84
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325916"
---
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a><span data-ttu-id="8ea49-103">Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny</span><span class="sxs-lookup"><span data-stu-id="8ea49-103">How to: Group Windows Forms RadioButton Controls to Function as a Set</span></span>
<span data-ttu-id="8ea49-104"><xref:System.Windows.Forms.RadioButton>Ovládací prvky model Windows Forms jsou navrženy tak, aby uživatelům poskytovaly možnost volby mezi dvěma nebo více nastaveními, z nichž lze přiřadit pouze jednu proceduru nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="8ea49-104">Windows Forms <xref:System.Windows.Forms.RadioButton> controls are designed to give users a choice among two or more settings, of which only one can be assigned to a procedure or object.</span></span> <span data-ttu-id="8ea49-105">Například skupina <xref:System.Windows.Forms.RadioButton> ovládacích prvků může zobrazit výběr nosičů balíčků pro objednávku, ale bude použit pouze jeden z dopravců.</span><span class="sxs-lookup"><span data-stu-id="8ea49-105">For example, a group of <xref:System.Windows.Forms.RadioButton> controls may display a choice of package carriers for an order, but only one of the carriers will be used.</span></span> <span data-ttu-id="8ea49-106">Proto <xref:System.Windows.Forms.RadioButton> lze vybrat pouze jednu v čase, a to i v případě, že je součástí funkční skupiny.</span><span class="sxs-lookup"><span data-stu-id="8ea49-106">Therefore only one <xref:System.Windows.Forms.RadioButton> at a time can be selected, even if it is a part of a functional group.</span></span>  
  
 <span data-ttu-id="8ea49-107">Přepínače můžete seskupovat tak, že je vykreslíte do kontejneru <xref:System.Windows.Forms.Panel> , jako je ovládací prvek, <xref:System.Windows.Forms.GroupBox> ovládací prvek nebo formulář.</span><span class="sxs-lookup"><span data-stu-id="8ea49-107">You group radio buttons by drawing them inside a container such as a <xref:System.Windows.Forms.Panel> control, a <xref:System.Windows.Forms.GroupBox> control, or a form.</span></span> <span data-ttu-id="8ea49-108">Všechna přepínací tlačítka, která jsou přidána přímo do formuláře, se stanou jednou skupinou.</span><span class="sxs-lookup"><span data-stu-id="8ea49-108">All radio buttons that are added directly to a form become one group.</span></span> <span data-ttu-id="8ea49-109">Chcete-li přidat samostatné skupiny, je nutné je umístit do panelů nebo skupinových polí.</span><span class="sxs-lookup"><span data-stu-id="8ea49-109">To add separate groups, you must place them inside panels or group boxes.</span></span> <span data-ttu-id="8ea49-110">Další informace o panelech nebo skupinových polích naleznete v tématu [Přehled ovládacího prvku panel](panel-control-overview-windows-forms.md) nebo [Přehled ovládacího prvku skupinový](groupbox-control-overview-windows-forms.md)odkaz.</span><span class="sxs-lookup"><span data-stu-id="8ea49-110">For more information about panels or group boxes, see [Panel Control Overview](panel-control-overview-windows-forms.md) or [GroupBox Control Overview](groupbox-control-overview-windows-forms.md).</span></span>  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a><span data-ttu-id="8ea49-111">Seskupení ovládacích prvků RadioButton jako sady funkcí nezávisle na jiných sadách</span><span class="sxs-lookup"><span data-stu-id="8ea49-111">To group RadioButton controls as a set to function independently of other sets</span></span>  
  
1. <span data-ttu-id="8ea49-112">Přetáhněte <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> ovládací prvek nebo z karty **model Windows Forms** na **panelu nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="8ea49-112">Drag a <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab on the **Toolbox** onto the form.</span></span>  
  
2. <span data-ttu-id="8ea49-113">Nakreslete <xref:System.Windows.Forms.RadioButton> ovládací prvky <xref:System.Windows.Forms.GroupBox> v <xref:System.Windows.Forms.Panel> ovládacím prvku nebo.</span><span class="sxs-lookup"><span data-stu-id="8ea49-113">Draw <xref:System.Windows.Forms.RadioButton> controls on the <xref:System.Windows.Forms.GroupBox> or <xref:System.Windows.Forms.Panel> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ea49-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ea49-114">See also</span></span>

- <xref:System.Windows.Forms.RadioButton>
- [<span data-ttu-id="8ea49-115">Přehled ovládacího prvku RadioButton</span><span class="sxs-lookup"><span data-stu-id="8ea49-115">RadioButton Control Overview</span></span>](radiobutton-control-overview-windows-forms.md)
- [<span data-ttu-id="8ea49-116">Přehled ovládacího prvku Panel</span><span class="sxs-lookup"><span data-stu-id="8ea49-116">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="8ea49-117">GroupBox – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8ea49-117">GroupBox Control Overview</span></span>](groupbox-control-overview-windows-forms.md)
- [<span data-ttu-id="8ea49-118">CheckBox – přehled ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="8ea49-118">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="8ea49-119">Ovládací prvek RadioButton</span><span class="sxs-lookup"><span data-stu-id="8ea49-119">RadioButton Control</span></span>](radiobutton-control-windows-forms.md)
