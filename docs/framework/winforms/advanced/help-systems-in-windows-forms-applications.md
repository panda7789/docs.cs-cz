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
ms.openlocfilehash: 0b5b9622eaa2dc9f4ade615f1c538db0bd15bc47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602270"
---
# <a name="help-systems-in-windows-forms-applications"></a>Systémy nápovědy ve formulářových aplikacích Windows
Jeden z vašich nejdůležitějších courtesies, jak pro vývojáře aplikací, můžete poskytnout uživatelům s je příslušný systém nápovědy. Je to, kde se změní při stát zaměňovat nebo disoriented. Poskytuje systém nápovědy v aplikaci založené na Windows se snadno provádí pomocí [HelpProvider – komponenta](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).  
  
## <a name="different-types-of-help"></a>Různé druhy nápovědy  
 Windows Forms <xref:System.Windows.Forms.HelpProvider> součást slouží k přidružení souboru nápovědy HTML Help 1.x (soubor CHM vytvořenými pomocí HTML Help Workshop, nebo soubor HTM) s vaší aplikací se systémem Windows. <xref:System.Windows.Forms.HelpProvider> Komponenty lze použít k poskytnutí kontextové nápovědy pro ovládacích prvků ve Windows Forms nebo konkrétní ovládací prvky. Kromě toho <xref:System.Windows.Forms.HelpProvider> součásti můžete otevřít soubor nápovědy pro konkrétní oblasti, jako je hlavní stránky tabulku z obsahu, index nebo vyhledávací funkci. Obecné informace o <xref:System.Windows.Forms.HelpProvider> komponenty, naleznete v tématu [HelpProvider – přehled komponenty](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md). Informace o tom, jak používat <xref:System.Windows.Forms.HelpProvider> součásti k zobrazení místní nápovědy v aplikaci Windows Forms, naleznete v tématu [jak: Zobrazení místní nápovědy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md). Informace o používání <xref:System.Windows.Forms.ToolTip> komponenta zobrazit nápovědu pro konkrétní správu, najdete v článku [popisky pomáhají pomocí ovládacího prvku](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).  
  
 Můžete generovat soubory nápovědy HTML 1.x s HTML Help Workshop. Další informace o Nápověda jazyka HTML naleznete v tématu "HTML Help Workshop" nebo v jiných tématech "HTML Help" na webu MSDN.  
  
## <a name="see-also"></a>Viz také:
- [Integrace uživatelské nápovědy v modelu Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)
- [Komponenta HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)
- [Komponenta ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
- [Přehled produktu Windows Forms](../../../../docs/framework/winforms/windows-forms-overview.md)
- [Windows Forms](../../../../docs/framework/winforms/index.md)
