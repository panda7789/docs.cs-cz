---
title: "ToolTip – přehled komponenty (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip – přehled komponenty (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ToolTip> součást zobrazí text, když uživatel odkazuje na ovládací prvky. Popisek může být přidružen žádný ovládací prvek. Příklad použití této součásti: ušetřit místo na formuláři, můžete zobrazení malé ikony na tlačítku a pomocí popisek vysvětlit funkce tlačítka.  
  
## <a name="working-with-the-tooltip-component"></a>Práce s komponentou ToolTip  
 A <xref:System.Windows.Forms.ToolTip> poskytuje součásti `ToolTip` vlastnosti tak, aby více ovládacích prvků na formuláři Windows nebo jiné kontejneru. Například, pokud umístíte jedno <xref:System.Windows.Forms.ToolTip> součást ve formuláři, můžete zobrazit "Zadejte zde název" <xref:System.Windows.Forms.TextBox> řízení a "Kliknutím sem uložte změny" pro <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
 Klíče metody <xref:System.Windows.Forms.ToolTip> jsou součástí <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> a <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>. Můžete použít <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodu pro nastavení ToolTips pro ovládací prvky zobrazen. Další informace najdete v tématu [postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md). Klíčové vlastnosti jsou <xref:System.Windows.Forms.ToolTip.Active%2A>, který musí být nastaven na `true` pro popisek, který se zobrazí, a <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, která nastaví dobu, která se zobrazí text popisu tlačítka, jak dlouho musí odkazovat uživatele v ovládacím prvku pro popisek, který se zobrazí a jak ho dlouhé potřebná pro následné popisku windows zobrazí. Další informace najdete v tématu [postupy: Změna zpoždění součásti Windows Forms ToolTip](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolTip>  
 [Postupy: nastavení ToolTips pro ovládací prvky na formuláři Windows v době návrhu](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [Postupy: Změna zpoždění součásti Windows Forms ToolTip](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
