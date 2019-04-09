---
title: ToolTip – přehled komponenty (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 3fbe883501d1ce36ca25ea07631f98042f451e07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197305"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> komponenty zobrazí text, když uživatel vybere na ovládací prvky. Popis tlačítka lze přidružit libovolný ovládací prvek. Příklad použití této součásti: pro úsporu místa ve formuláři, můžete zobrazit malé ikony na tlačítku a vysvětlují funkce tlačítka pomocí popisek.  
  
## <a name="working-with-the-tooltip-component"></a>Práce s ToolTip – komponenta  
 A <xref:System.Windows.Forms.ToolTip> součást poskytuje `ToolTip` vlastnost má více ovládacích prvků ve formuláři Windows nebo jiném kontejneru. Například pokud jedna <xref:System.Windows.Forms.ToolTip> komponenty ve formuláři, můžete zobrazit "Zadejte sem patří vaše jméno" pro <xref:System.Windows.Forms.TextBox> řídit a "Kliknutím sem uložte změny" pro <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
 Klíče metody <xref:System.Windows.Forms.ToolTip> komponenty jsou <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> a <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Můžete použít <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu pro nastavení ToolTips pro ovládací prvky zobrazí. Další informace najdete v tématu [jak: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Jsou klíčové vlastnosti <xref:System.Windows.Forms.ToolTip.Active%2A>, musí být nastaveno na `true` pro popisek, který se zobrazí, a <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, který nastaví dobu, která se zobrazí řetězec popisku, jak dlouho musí odkazovat uživatele v ovládacím prvku pro popisek, který se zobrazí a jak dlouhé je potřebná pro následné okna s popisem tlačítek se zobrazí. Další informace najdete v tématu [jak: Změna zpoždění komponenty Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolTip>
- [Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Postupy: Změna zpoždění komponenty Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
