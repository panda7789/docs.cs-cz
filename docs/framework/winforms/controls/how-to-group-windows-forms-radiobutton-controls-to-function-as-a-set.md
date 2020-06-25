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
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny
<xref:System.Windows.Forms.RadioButton>Ovládací prvky model Windows Forms jsou navrženy tak, aby uživatelům poskytovaly možnost volby mezi dvěma nebo více nastaveními, z nichž lze přiřadit pouze jednu proceduru nebo objekt. Například skupina <xref:System.Windows.Forms.RadioButton> ovládacích prvků může zobrazit výběr nosičů balíčků pro objednávku, ale bude použit pouze jeden z dopravců. Proto <xref:System.Windows.Forms.RadioButton> lze vybrat pouze jednu v čase, a to i v případě, že je součástí funkční skupiny.  
  
 Přepínače můžete seskupovat tak, že je vykreslíte do kontejneru <xref:System.Windows.Forms.Panel> , jako je ovládací prvek, <xref:System.Windows.Forms.GroupBox> ovládací prvek nebo formulář. Všechna přepínací tlačítka, která jsou přidána přímo do formuláře, se stanou jednou skupinou. Chcete-li přidat samostatné skupiny, je nutné je umístit do panelů nebo skupinových polí. Další informace o panelech nebo skupinových polích naleznete v tématu [Přehled ovládacího prvku panel](panel-control-overview-windows-forms.md) nebo [Přehled ovládacího prvku skupinový](groupbox-control-overview-windows-forms.md)odkaz.  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Seskupení ovládacích prvků RadioButton jako sady funkcí nezávisle na jiných sadách  
  
1. Přetáhněte <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Panel> ovládací prvek nebo z karty **model Windows Forms** na **panelu nástrojů** do formuláře.  
  
2. Nakreslete <xref:System.Windows.Forms.RadioButton> ovládací prvky <xref:System.Windows.Forms.GroupBox> v <xref:System.Windows.Forms.Panel> ovládacím prvku nebo.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.RadioButton>
- [Přehled ovládacího prvku RadioButton](radiobutton-control-overview-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [GroupBox – přehled ovládacího prvku](groupbox-control-overview-windows-forms.md)
- [CheckBox – přehled ovládacího prvku](checkbox-control-overview-windows-forms.md)
- [Ovládací prvek RadioButton](radiobutton-control-windows-forms.md)
