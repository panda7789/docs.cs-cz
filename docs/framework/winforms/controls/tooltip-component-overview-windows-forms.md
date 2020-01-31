---
title: ToolTip – přehled komponenty
ms.date: 03/30/2017
f1_keywords:
- ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
ms.openlocfilehash: 731f7ad0ce6670000d8c3d3e901e1506f7ef470a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741900"
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip – přehled komponenty (Windows Forms)
Komponenta model Windows Forms <xref:System.Windows.Forms.ToolTip> zobrazí text, když uživatel ukáže na ovládacím prvku. Popisek lze přidružit k libovolnému ovládacímu prvku. Příklad použití této součásti: Chcete-li ušetřit místo na formuláři, můžete zobrazit malou ikonu tlačítka a použít popis k vysvětlení funkce tlačítka.  
  
## <a name="working-with-the-tooltip-component"></a>Práce s komponentou ToolTip  
 Komponenta <xref:System.Windows.Forms.ToolTip> poskytuje vlastnost `ToolTip` pro více ovládacích prvků ve formuláři Windows nebo v jiném kontejneru. Pokud například umístíte jednu komponentu <xref:System.Windows.Forms.ToolTip> do formuláře, můžete pro ovládací prvek <xref:System.Windows.Forms.TextBox> zobrazit "sem zadejte své jméno" a "kliknutím sem uložíte změny" pro ovládací prvek <xref:System.Windows.Forms.Button>.  
  
 Klíčové metody součásti <xref:System.Windows.Forms.ToolTip> jsou <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> a <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Pomocí metody <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> lze nastavit popisy tlačítek zobrazených pro ovládací prvky. Další informace najdete v tématu [Postup: nastavení popisů ovládacích prvků pro ovládací prvky ve formuláři Windows v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Klíčové vlastnosti jsou <xref:System.Windows.Forms.ToolTip.Active%2A>, které musí být nastavené na `true` pro zobrazení popisu tlačítka, a <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, která nastavuje dobu, po kterou je zobrazen řetězec s popisem, jak dlouho musí uživatel ukazovat na ovládací prvek ToolTip a jak dlouho se má zobrazit další okna s popisem tlačítka. Další informace najdete v tématu [Postup: Změna zpoždění součásti model Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolTip>
- [Postupy: Nastavení ToolTips pro ovládací prvky ve formuláři Windows Forms v době návrhu](how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)
- [Postupy: Změna zpoždění komponenty Windows Forms ToolTip](how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
