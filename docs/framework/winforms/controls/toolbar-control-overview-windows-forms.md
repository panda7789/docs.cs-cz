---
title: "ToolBar – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ToolBar
helpviewer_keywords:
- toolbars [Windows Forms], about toolbars
- ToolBar control [Windows Forms], about ToolBar controls
ms.assetid: d426b203-0216-4dbe-b834-1641e50a9c29
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eac54e18f397cf455ffd5fa33c2e000d87b917a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="toolbar-control-overview-windows-forms"></a>ToolBar – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 Windows Forms <xref:System.Windows.Forms.ToolBar> řízení se používá ve formulářích jako ovládací prvek panel, který zobrazí řádek rozevíracích nabídek a rastrové tlačítka, který aktivovat příkazy. Kliknutím na tlačítko panelu nástrojů proto může být ekvivalentní k výběru příkazu nabídky. Tlačítka lze nastavit zobrazit, a chovat jako tlačítek, rozevíracích nabídek nebo oddělovače. Panel nástrojů obvykle obsahuje tlačítka a nabídky, které odpovídají položkám v nabídce struktura aplikace, poskytující rychlý přístup aplikaci nejčastěji používaných funkcí a příkazy.  
  
## <a name="working-with-the-toolbar-control"></a>Práce s ovládacím prvkem panel nástrojů  
 A <xref:System.Windows.Forms.ToolBar> řízení obvykle "ukotven" v horní části jeho nadřazeného okna, ale lze ukotvit také na žádné straně okna. Panel nástrojů můžete zobrazí popisy ovládacích prvků, když uživatel vybere ukazatel myši na tlačítka panelu nástrojů. Popisek je malé místní okno, která stručně popisuje tlačítko nebo nabídky účel. Chcete-li zobrazit popisy tlačítek, <xref:System.Windows.Forms.ToolBar.ShowToolTips%2A> musí být nastavena na `true`.  
  
> [!NOTE]
>  Některé aplikace funkce prvky velmi podobná panelu nástrojů, které mají možnost "float" nad okna aplikace a změnit jejich umístění. Ovládací prvek panelu nástrojů Windows Forms není možné provést tyto akce.  
  
 Když <xref:System.Windows.Forms.ToolBar.Appearance%2A> je nastavena na <xref:System.Windows.Forms.ToolBarAppearance>, tlačítka panelu nástrojů zobrazí trojrozměrné a nevyskytla se. Můžete nastavit <xref:System.Windows.Forms.ToolBar.Appearance%2A> vlastnost panelu nástrojů <xref:System.Windows.Forms.ToolBarAppearance> umožnit jeho tlačítka panelu nástrojů a s plochým vzhledem. Při přesunutí ukazatele myši ploché tlačítko, vzhled tlačítka se změní na trojrozměrné. Tlačítka panelu nástrojů je možné rozdělit do logických skupin s použitím oddělovače. Oddělovač je tlačítko panelu nástrojů s <xref:System.Windows.Forms.ToolBarButton.Style%2A> vlastnost nastavena na hodnotu <xref:System.Windows.Forms.ToolBarButtonStyle>. Zobrazí se jako prázdné místo na panelu nástrojů. Pokud panelu nástrojů jako plochá, oddělovače tlačítko se zobrazí jako řádky spíše než mezery mezi tlačítka.  
  
 <xref:System.Windows.Forms.ToolBar> Řízení vám umožní vytvořit panely nástrojů přidáním <xref:System.Windows.Forms.Button> objekty do <xref:System.Windows.Forms.ToolBar.Buttons%2A> kolekce. Editor kolekce můžete přidávat tlačítka <xref:System.Windows.Forms.ToolBar> řízení; každá <xref:System.Windows.Forms.Button> objekt by měl mít text nebo bitovou kopii přiřazen, i když můžete přiřadit i. Poskytnutý bitovou kopii podle přidružené [ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) součásti. V době běhu, můžete přidat nebo odebrat tlačítka z <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection> pomocí <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Add%2A> a <xref:System.Windows.Forms.ToolBar.ToolBarButtonCollection.Remove%2A> metody. Do programu tlačítka z <xref:System.Windows.Forms.ToolBar>, přidejte kód, který <xref:System.Windows.Forms.ToolBar.ButtonClick> události <xref:System.Windows.Forms.ToolBar>pomocí <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vlastnost <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídu k určení, které tlačítko bylo kliknuto.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolBar>  
 [Ovládací prvek ToolBar](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [Postupy: Definování ikony pro tlačítko ToolBar](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)
