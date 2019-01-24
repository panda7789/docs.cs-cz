---
title: Slučování položek nabídky v ovládacím prvku Windows Forms MenuStrip
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 96168c197771cbfebf3a090ac236b21e487cb3a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551849"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Slučování položek nabídky v ovládacím prvku Windows Forms MenuStrip
Pokud máte aplikace rozhraní více dokumentů (MDI), můžete sloučit položky nabídky nebo celý nabídek z podřízeného formuláře do nabídky nadřazeného formuláře.  
  
 Toto téma popisuje základní koncepty přidružených ke slučování položek nabídky v aplikaci MDI.  
  
## <a name="general-concepts"></a>Obecné koncepty  
 Sloučení postupy zahrnují cíl a správy zdrojového kódu:  
  
-   Cílem <xref:System.Windows.Forms.MenuStrip> ovládací prvek na hlavní nebo nadřazený formulář MDI, do které provádíte sloučení položek nabídky.  
  
-   Zdroj je <xref:System.Windows.Forms.MenuStrip> ovládací prvek na podřízený formulář MDI, která obsahuje položky nabídky, které chcete sloučit do nabídky Cíl.  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> Vlastnost identifikuje položku nabídky, jehož rozevíracího seznamu naplníte názvy aktuální MDI nadřazené podřízené formuláře MDI. Například můžete obvykle podřízený objekt MDI, které jsou právě otevřeny na seznam **okno** nabídky.  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> Vlastnost určuje, které pochází položky nabídky <xref:System.Windows.Forms.MenuStrip> na podřízený formulář MDI.  
  
 Položky nabídky můžete sloučit ručně nebo automaticky. Sloučení položek nabídky, stejně jako u obou metod, ale sloučení se aktivuje jiným způsobem, jak je popsáno v části "Ruční sloučení" a "Automatického sloučení" dále v tomto tématu. V ručního a automatického sloučení, ovlivňuje všechny akce sloučení další akce sloučení.  
  
 <xref:System.Windows.Forms.MenuStrip> Slučování položek nabídky přesune z jedné <xref:System.Windows.Forms.ToolStrip> na jiné místo, klonování, stejně jako v případě s <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>MergeAction hodnoty  
 Nastavte akci sloučení položek nabídky ve zdroji <xref:System.Windows.Forms.MenuStrip> pomocí <xref:System.Windows.Forms.MergeAction> vlastnost.  
  
 Následující tabulka popisuje význam a typické použití akce k dispozici sloučení.  
  
|Hodnota MergeAction|Popis|Typické použití|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(Výchozí) Zdrojová položka přidá na konec cílové položky kolekce.|Přidání položky nabídky na konec objektu v nabídce při aktivaci některé části tohoto programu.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Přidá položku zdrojové do cílové položky kolekce, v místě určeném <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> nastavenou na zdroj položky.|Přidání položek nabídky do středu nebo na začátku nabídce při aktivaci některé části tohoto programu.<br /><br /> Pokud hodnota <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> je stejný pro obě položky nabídky, se přidají v obráceném pořadí. Nastavte <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> správně zachovat původní pořadí.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Najde shodu text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud žádná shoda text nenajde a pak nahradí odpovídající cílové položky nabídky Zdroj položky nabídky.|Cílová položka nabídky nahradíte zdroj položky nabídky se stejným názvem, který provede něco jiného.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Najde shodu text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud neodpovídá text nenajde a pak přidá všechny rozevírací položky ze zdroje do cíle.|Sestavování struktura nabídky, která vloží přidá položky nabídky do podnabídky nebo odebere položky nabídky z podnabídky. Například můžete přidat položku nabídky z podřízeného MDI do hlavního <xref:System.Windows.Forms.MenuStrip> **uložit jako** nabídky.<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> Umožňuje procházet struktura nabídky bez nutnosti přepínat žádnou akci. Poskytuje způsob, jak vyhodnotit následující položky.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Najde shodu text nebo používá <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud neodpovídá text nachází a pak taky odebere položku z cíle.|Odebrání položky nabídky z cíle <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Ruční sloučení  
 Pouze <xref:System.Windows.Forms.MenuStrip> ovládací prvky, které jsou součástí automatického sloučení. Ke sloučení položky další ovládací prvky, jako například <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky, musíte sloučit je ručně, voláním <xref:System.Windows.Forms.ToolStripManager.Merge%2A> a <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> metody v kódu podle potřeby.  
  
## <a name="automatic-merging"></a>Automatické sloučení  
 Můžete použít automatické sloučení pro aplikace MDI aktivací zdrojové formě. Použití <xref:System.Windows.Forms.MenuStrip> v aplikaci MDI, nastavte <xref:System.Windows.Forms.Form.MainMenuStrip%2A> vlastnost k cíli <xref:System.Windows.Forms.MenuStrip> tak, aby sloučení akce provedené na zdroji <xref:System.Windows.Forms.MenuStrip> se odrazí v cílové <xref:System.Windows.Forms.MenuStrip>.  
  
 Můžete aktivovat pomocí aktivace automatického sloučení <xref:System.Windows.Forms.MenuStrip> ve zdroji MDI. Po aktivaci, zdroj <xref:System.Windows.Forms.MenuStrip> se sloučí do cílové MDI. Po aktivaci nového formuláře, sloučení je vrátit zpět na poslední formulář a aktivovat na nový formulář. Toto chování můžete ovládat nastavením <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> vlastnosti podle potřeby v každém <xref:System.Windows.Forms.ToolStripItem>a tím, že nastavíte <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> vlastnost na každém <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
- [Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Postupy: Nastavení automatického slučování nabídek pro aplikace MDI](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
