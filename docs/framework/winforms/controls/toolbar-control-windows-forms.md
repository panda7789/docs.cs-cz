---
title: ToolBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 8162dfc898f7965d65de918d2a5b1f7afbfdf9b2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863280"
---
# <a name="toolbar-control-windows-forms"></a>ToolBar – ovládací prvek (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které `ToolBar` řízení; však `ToolBar` ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 Windows Forms `ToolBar` ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek z rozevírací nabídky a tlačítek s rastrovými obrázky, které aktivovat příkazy. Kliknutím na tlačítko panelu nástrojů je tedy ekvivalentem možnosti vybrání příkazu nabídky. Tlačítka lze nastavit na a chovají se jako tlačítek, rozevíracích nabídek nebo oddělovače. Obvykle obsahuje panel nástrojů tlačítka a nabídky, které odpovídají položky nabídky struktury aplikace poskytuje rychlý přístup k aplikačním nejčastěji používané funkce a příkazy.  
  
> [!NOTE]
>  `ToolBar` Ovládacího prvku <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> vlastnost přebírá instanci <xref:System.Windows.Forms.ContextMenu> třídu jako odkaz. Pečlivě zvažte, předáte při implementaci tohoto druhu tlačítko na panely nástrojů v aplikaci jako vlastnost přijme některý objekt, který dědí z odkazu <xref:System.Windows.Forms.Menu> třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 Představuje obecné koncepty `ToolBar` ovládací prvek, který vám umožní navrhnout vlastní panely nástrojů, které vaši uživatelé můžou pracovat s.  
  
 [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 Popisuje postup přidání tlačítek `ToolBar` ovládacího prvku.  
  
 [Postupy: Definování ikony pro tlačítko ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 Popisuje, jak zobrazit ikony v rámci `ToolBar` ovládacího prvku tlačítka.  
  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Poskytuje pokyny s psaním kódu pro interpretaci, které uživatel tlačítko klikne do oblasti `ToolBar` ovládacího prvku.  
  
 Také naleznete v tématu [postupy: definování ikony pro panelu nástrojů tlačítko pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [postupy: Přidání tlačítka na panelu nástrojů ovládacího prvku pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.ToolBar> Třída  
 Poskytuje referenční informace o třídě a její členy.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Obsahuje úplný seznam všech ovládacích prvcích Windows Forms, s odkazy na informace o jejich použití.  
  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 Popisuje panely nástrojů, které můžete hostovat nabídek, ovládacích prvků a uživatelských ovládacích prvků v aplikacích Windows Forms.
