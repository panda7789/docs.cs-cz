---
title: ToolBar – ovládací prvek
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolBar control [Windows Forms]
ms.assetid: 6b40e9ce-6a7a-4784-bfc9-7f1d36b7462e
ms.openlocfilehash: 027c96bb49e9446244e4b08ba93c551ef043b3c0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735464"
---
# <a name="toolbar-control-windows-forms"></a>ToolBar – ovládací prvek (Windows Forms)
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.ToolStrip> nahrazuje a přidává funkce do ovládacího prvku `ToolBar`; Nicméně ovládací prvek `ToolBar` se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Ovládací prvek model Windows Forms `ToolBar` se ve formulářích používá jako ovládací panel, který zobrazuje řádek rozevíracích nabídek a tlačítek s rastrovými obrázky, které aktivují příkazy. Kliknutí na tlačítko na panelu nástrojů je tedy ekvivalentní k výběru příkazu nabídky. Tlačítka se dají nakonfigurovat tak, aby se zobrazovala jako tlačítka pro vložení, rozevírací nabídky nebo oddělovače. Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v rámci struktury nabídky aplikace, a poskytuje tak rychlý přístup k nejčastěji používaným funkcím a příkazům aplikace.  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A> ovládacího prvku `ToolBar` přebírá instanci třídy <xref:System.Windows.Forms.ContextMenu> jako referenci. Pečlivě zvažte odkaz, který předáte při implementaci tohoto tlačítka na panelech nástrojů ve vaší aplikaci, protože vlastnost akceptuje libovolný objekt, který dědí z třídy <xref:System.Windows.Forms.Menu>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku ToolBar](toolbar-control-overview-windows-forms.md)  
 Zavádí obecné koncepce ovládacího prvku `ToolBar`, který umožňuje navrhovat vlastní panely nástrojů, se kterými můžou uživatelé pracovat.  
  
 [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md)  
 Popisuje, jak přidat tlačítka do ovládacího prvku `ToolBar`.  
  
 [Postupy: Definování ikony pro tlačítko ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)  
 Popisuje, jak zobrazit ikony v rámci tlačítek ovládacího prvku `ToolBar`.  
  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](how-to-trigger-menu-events-for-toolbar-buttons.md)  
 Poskytuje pokyny k psaní kódu pro interpretaci, které tlačítko uživatel klikne v ovládacím prvku `ToolBar`.  
  
 Viz také [Postupy: definování ikony pro tlačítko panelu nástrojů pomocí návrháře](how-to-define-an-icon-for-a-toolbar-button-using-the-designer.md), [Postupy: Přidání tlačítek do ovládacího prvku panelu nástrojů pomocí návrháře](how-to-add-buttons-to-a-toolbar-control-using-the-designer.md).  
  
## <a name="reference"></a>Referenční informace  
 Třída <xref:System.Windows.Forms.ToolBar>  
 Poskytuje referenční informace o třídě a jejích členech.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)  
 Obsahuje úplný seznam model Windows Formsch ovládacích prvků s odkazy na informace o jejich použití.  
  
 [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)  
 Popisuje panely nástrojů, které mohou hostovat nabídky, ovládací prvky a uživatelské ovládací prvky v aplikacích model Windows Forms.
