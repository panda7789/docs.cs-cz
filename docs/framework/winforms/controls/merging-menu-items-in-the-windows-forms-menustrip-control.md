---
title: "Slučování položek nabídky v ovládacím prvku Windows Forms MenuStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8e042b3f7b0a2a2e40b8fba33fca6c147086df6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Slučování položek nabídky v ovládacím prvku Windows Forms MenuStrip
Pokud máte aplikace rozhraní více dokumentů (MDI), můžete sloučit položky nabídky nebo celý nabídky z podřízené formuláře do nabídky nadřazeného formuláře.  
  
 Toto téma popisuje základní koncepce aplikace sloučení položek nabídky v aplikaci MDI.  
  
## <a name="general-concepts"></a>Obecné koncepty  
 Slučovat postupy zahrnují cíl a Správa zdrojového kódu:  
  
-   Cíl je <xref:System.Windows.Forms.MenuStrip> ovládací prvek v hlavní nebo nadřazeného formuláře MDI, do kterého jsou sloučení položek nabídky.  
  
-   Zdroj je <xref:System.Windows.Forms.MenuStrip> ovládacího prvku formuláře MDI podřízené, který obsahuje položky nabídky, které chcete ke sloučení do nabídky Cíl.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Vlastnost identifikuje položku nabídky, jejichž rozevíracího seznamu zaplníte s názvy aktuální MDI nadřazené formuláře MDI podřízené objekty. Například můžete obvykle MDI podřízené objekty, které jsou aktuálně otevřené na seznam **okno** nabídky.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Vlastnost uvedeno, které pocházejí položek nabídky <xref:System.Windows.Forms.MenuStrip> na podřízené formuláře MDI.  
  
 Položky nabídky můžete sloučit ručně nebo automaticky. Sloučení položek nabídky v stejným způsobem jako u obou metod, ale sloučení se aktivuje odlišně, jak je popsáno v části "Ruční sloučení" a "Automatického slučování" dál v tomto tématu. Každá akce sloučení v ručního a automatického slučování, ovlivňuje další akce sloučení.  
  
 <xref:System.Windows.Forms.MenuStrip>sloučení položek nabídky přesune z jednoho <xref:System.Windows.Forms.ToolStrip> na jiné místo klonování, stejně jako v případě s <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>MergeAction hodnoty  
 Nastavíte akce sloučení položek nabídky v zdroji <xref:System.Windows.Forms.MenuStrip> pomocí <xref:System.Windows.Forms.MergeAction> vlastnost.  
  
 Následující tabulka popisuje znamená a typické použití akce k dispozici sloučení.  
  
|Hodnota MergeAction|Popis|Typické použití|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Výchozí) Přidá zdroj položku na konec kolekce položek cíl.|Přidání položek nabídky na konec v nabídce, když je aktivován některých součástí programu.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Přidá zdroj položku do kolekce cílová položka v umístění, které <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> vlastnost nastavte u položky zdroje.|Přidání položek nabídky na střed nebo na začátku v nabídce, když je aktivován některých součástí programu.<br /><br /> Pokud hodnota <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> je stejný pro obě položky nabídky, přidají se v obráceném pořadí. Nastavit <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> správně zachovat původní pořadí.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Najde odpovídající text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud žádná shoda text nenajde a odpovídající položky nabídky Cíl nahradí položku nabídky zdroje.|Nahraďte položku nabídky Cíl s položku nabídky zdroje se stejným názvem, který nemá něco jiného.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Najde odpovídající text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud žádná shoda text nenajde a potom přidá všechny položky rozevíracího seznamu ve zdroji k cíli.|Vytváření struktury nabídky, která vloží nebo přidá položek nabídky do podnabídky nebo odebere podnabídky položky nabídky. Například můžete přidat položku nabídky z podřízeného MDI do hlavního <xref:System.Windows.Forms.MenuStrip> **uložit jako** nabídky.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly>Umožňuje procházet strukturou nabídky bez provedení akce. Poskytuje způsob, jak vyhodnotit dalších položek.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Najde odpovídající text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud žádná shoda textu se nachází a pak odebere položku z cíle.|Odebrání položky nabídky z cíle <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Ruční sloučení  
 Pouze <xref:System.Windows.Forms.MenuStrip> ovládací prvky účastnit automatického slučování. Kombinovat položky další ovládací prvky, jako například <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky, musí jejich sloučení ručně voláním <xref:System.Windows.Forms.ToolStripManager.Merge%2A> a <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> metody ve vašem kódu podle potřeby.  
  
## <a name="automatic-merging"></a>Automatické sloučení  
 Můžete použít automatické sloučení pro aplikace MDI aktivací formuláře zdroje. Použít <xref:System.Windows.Forms.MenuStrip> v aplikaci MDI nastavit <xref:System.Windows.Forms.Form.MainMenuStrip%2A> vlastnost k cíli <xref:System.Windows.Forms.MenuStrip> tak, aby slučování akce provést ve zdroji <xref:System.Windows.Forms.MenuStrip> se odrazí v cílové <xref:System.Windows.Forms.MenuStrip>.  
  
 Můžete aktivovat automatického slučování aktivací <xref:System.Windows.Forms.MenuStrip> ve zdroji MDI. Po aktivaci, zdroj <xref:System.Windows.Forms.MenuStrip> sloučí MDI cíl. Po aktivaci nového formuláře, sloučení je vrátit zpět na poslední formuláři a aktivována nového formuláře. Toto chování můžete ovládat nastavením <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> vlastnost podle potřeby na každém <xref:System.Windows.Forms.ToolStripItem>a nastavením <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost na každém <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip – ovládací prvek](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Postupy: vytvoření seznamu okna MDI pomocí MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [Postupy: nastavení automatického slučování nabídek pro aplikace MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
