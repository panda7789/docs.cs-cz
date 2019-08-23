---
title: ToolBar – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 13a56af0e52897a6fd4e11516fbf4c0b8f6d6b5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929570"
---
# <a name="toolbar-control-windows-forms"></a>ToolBar – ovládací prvek (Windows Forms)
> [!NOTE]
> Ovládací prvek nahrazuje a přidává funkce `ToolBar` `ToolBar` ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStrip>  
  
 Model Windows Forms `ToolBar` ovládací prvek se používá ve formulářích jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy. Kliknutí na tlačítko na panelu nástrojů je tedy ekvivalentní k výběru příkazu nabídky. Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako tlačítka pro vložení, rozevírací nabídky nebo oddělovače. Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.  
  
> [!NOTE]
> Vlastnost<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> ovládacího prvku přebírá instanci <xref:System.Windows.Forms.ContextMenu>třídy `ToolBar` jako referenci. Pečlivě zvažte odkaz, který předáte při implementaci tohoto tlačítka na panelech nástrojů ve vaší aplikaci, protože vlastnost akceptuje libovolný objekt, který dědí z <xref:System.Windows.Forms.Menu> třídy.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku ToolBar](toolbar-control-overview-windows-forms.md)  
 Zavádí obecné koncepce `ToolBar` ovládacího prvku, které vám umožní navrhnout vlastní panely nástrojů, se kterými uživatelé můžou pracovat.  
  
 [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md)  
 Popisuje, jak přidat tlačítka do `ToolBar` ovládacího prvku.  
  
 [Postupy: Definování ikony pro tlačítko panelu nástrojů](how-to-define-an-icon-for-a-toolbar-button.md)  
 Popisuje, jak zobrazit ikony v rámci `ToolBar` tlačítek ovládacího prvku.  
  
 [Postupy: Aktivace událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Poskytuje pokyny k psaní kódu pro interpretaci, na které tlačítko uživatel klikne v `ToolBar` ovládacím prvku.  
  
 Podívejte [se také na postupy: Definujte ikonu pro tlačítko panelu nástrojů pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [jak: Přidejte tlačítka do ovládacího prvku ToolBar pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).  
  
## <a name="reference"></a>Reference  
 <xref:System.Windows.Forms.ToolBar>Deník  
 Poskytuje referenční informace o třídě a jejích členech.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)  
 Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.  
  
 [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)  
 Popisuje panely nástrojů, které mohou hostovat nabídky, ovládací prvky a uživatelské ovládací prvky v aplikacích model Windows Forms.
