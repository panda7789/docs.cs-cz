---
title: Systémy nápovědy ve formulářových aplikacích Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: 293e6ecda3d763a4526349ee164d87da62f5e36d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="help-systems-in-windows-forms-applications"></a>Systémy nápovědy ve formulářových aplikacích Windows
Jeden z nejdůležitějších courtesies, jako vývojář aplikací, můžete poskytnout uživatelům bez je příslušný systém nápovědy. Toto je, kde bude zapnout když stát nerozumíte nebo disoriented. Poskytnutí systému nápovědy v aplikaci systému Windows se snadno provádí pomocí [HelpProvider – komponenta](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).  
  
## <a name="different-types-of-help"></a>Různé typy nápovědy  
 Windows Forms <xref:System.Windows.Forms.HelpProvider> součást je použit k přidružení soubor nápovědy HTML – Nápověda 1.x (soubor CHM. vytvořeného s pracoviště Nápověda HTML nebo soubor HTM) s vaší aplikací systému Windows. <xref:System.Windows.Forms.HelpProvider> Součást lze použít pro zajištění Kontextová nápověda ve Windows Forms – ovládací prvky nebo konkrétní ovládací prvky. Kromě toho <xref:System.Windows.Forms.HelpProvider> součást můžete otevřít soubor nápovědy pro konkrétní oblasti, například na hlavní stránku tabulky obsahu, indexu nebo funkce vyhledávání. Obecné informace o <xref:System.Windows.Forms.HelpProvider> součást, najdete v části [HelpProvider – přehled komponenty](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md). Informace o tom, jak používat <xref:System.Windows.Forms.HelpProvider> součásti pro zobrazení místní nápovědy v aplikaci Windows Forms, najdete v části [postupy: zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md). Informace o používání <xref:System.Windows.Forms.ToolTip> součást zobrazit nápovědu specifické pro ovládací prvek, najdete v části [ToolTips pomoci pomocí ovládacího prvku](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).  
  
 Soubory nápovědy HTML 1.x s pracoviště Nápověda HTML můžete vygenerovat. Další informace o HTML – Nápověda najdete v části "HTML pomůže pracoviště" nebo na další témata "HTML – Nápověda" na webu MSDN.  
  
## <a name="see-also"></a>Viz také  
 [Integrace uživatelské nápovědy v modelu Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Komponenta HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [Komponenta ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [Přehled produktu Windows Forms](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
