---
title: Systémy pro usnadnění
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
ms.openlocfilehash: c97a22dbdbdcc0eb282b52e16c4ef40914b1d9e7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742245"
---
# <a name="help-systems-in-windows-forms-applications"></a>Systémy nápovědy ve formulářových aplikacích Windows
Jedním z nejdůležitějších courtesies, jako vývojář aplikací, je poskytnout vašim uživatelům příslušný systém pro podporu. V takovém případě se zamění, když se stanou zaměňovánými nebo neorientovanými. Poskytnutí systému help v aplikaci pro systém Windows je snadné pomocí [komponenty HelpProvider –](../controls/helpprovider-component-windows-forms.md).  
  
## <a name="different-types-of-help"></a>Různé typy pomocníka  
 Komponenta model Windows Forms <xref:System.Windows.Forms.HelpProvider> se používá k přidružení souboru Help HTML 1. x (soubor s příponou. chm vytvořeného pomocí HTML Help Workshop nebo souboru. htm) s vaší aplikací založenou na Windows. Komponentu <xref:System.Windows.Forms.HelpProvider> lze použít k poskytnutí kontextové nápovědu pro ovládací prvky pro model Windows Forms nebo konkrétní ovládací prvky. Kromě toho může součást <xref:System.Windows.Forms.HelpProvider> otevřít soubor nápovědy pro konkrétní oblasti, jako je například hlavní stránka obsahu, index nebo funkce hledání. Obecné informace o komponentě <xref:System.Windows.Forms.HelpProvider> najdete v tématu [Přehled komponent HelpProvider –](../controls/helpprovider-component-overview-windows-forms.md). Informace o použití <xref:System.Windows.Forms.HelpProvider> komponenty k zobrazení místní nápovědy v model Windows Forms naleznete v tématu [How to: Display](how-to-display-pop-up-help.md)Informed help. Informace o použití součásti <xref:System.Windows.Forms.ToolTip> k zobrazení nápovědy pro konkrétní ovládací prvky najdete v tématu [Nápověda k ovládacímu prvku pomocí popisů tlačítek](control-help-using-tooltips.md).  
  
 Můžete generovat soubory HTML Help 1. x pomocí HTML Help Workshop. Další informace o nápovědě HTML naleznete v tématu "HTML Help Workshop" nebo v jiných tématech nápovědy "HTML" na webu MSDN.  
  
## <a name="see-also"></a>Viz také:

- [Integrace uživatelské nápovědy v modelu Windows Forms](integrating-user-help-in-windows-forms.md)
- [Komponenta HelpProvider](../controls/helpprovider-component-windows-forms.md)
- [Komponenta ToolTip](../controls/tooltip-component-windows-forms.md)
- [Přehled produktu Windows Forms](../windows-forms-overview.md)
- [Windows Forms](../index.md)
