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
# <a name="how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set"></a>Postupy: Seskupení ovládacích prvků Windows Forms RadioButton do funkce v podobě skupiny
Ovládací prvky model Windows Forms <xref:System.Windows.Forms.RadioButton> jsou navržené tak, aby uživatelům poskytovaly možnost volby mezi dvěma nebo více nastaveními, z nichž je možné přiřadit jenom jednu proceduru nebo objekt. Například skupina ovládacích prvků <xref:System.Windows.Forms.RadioButton> může zobrazit výběr nosičů balíčků pro objednávku, ale budou použity pouze jeden z dopravců. Proto lze vybrat pouze jeden <xref:System.Windows.Forms.RadioButton> v jednom okamžiku, i když je součástí funkční skupiny.  
  
 Přepínače můžete seskupovat tak, že je vykreslíte do kontejneru, jako je <xref:System.Windows.Forms.Panel> ovládací prvek, ovládací prvek <xref:System.Windows.Forms.GroupBox> nebo formulář. Všechna přepínací tlačítka, která jsou přidána přímo do formuláře, se stanou jednou skupinou. Chcete-li přidat samostatné skupiny, je nutné je umístit do panelů nebo skupinových polí. Další informace o panelech nebo skupinových polích naleznete v tématu [Přehled ovládacího prvku panel](panel-control-overview-windows-forms.md) nebo [Přehled ovládacího prvku skupinový](groupbox-control-overview-windows-forms.md)odkaz.  
  
### <a name="to-group-radiobutton-controls-as-a-set-to-function-independently-of-other-sets"></a>Seskupení ovládacích prvků RadioButton jako sady funkcí nezávisle na jiných sadách  
  
1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel> z karty **model Windows Forms** na **panelu nástrojů** do formuláře.  
  
2. Nakreslete ovládací prvky <xref:System.Windows.Forms.RadioButton> ovládacího prvku <xref:System.Windows.Forms.GroupBox> nebo <xref:System.Windows.Forms.Panel>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.RadioButton>
- [Přehled ovládacího prvku RadioButton](radiobutton-control-overview-windows-forms.md)
- [Přehled ovládacího prvku Panel](panel-control-overview-windows-forms.md)
- [Přehled ovládacího prvku GroupBox](groupbox-control-overview-windows-forms.md)
- [Přehled ovládacího prvku CheckBox](checkbox-control-overview-windows-forms.md)
- [Ovládací prvek RadioButton](radiobutton-control-windows-forms.md)
