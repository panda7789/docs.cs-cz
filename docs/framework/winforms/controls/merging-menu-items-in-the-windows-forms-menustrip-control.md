---
title: Sloučení položek nabídky v ovládacím prvku MenuStrip
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 9fc2b40ef23d72db51853c124095b734a7646cda
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739051"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Slučování položek nabídky v ovládacím prvku Windows Forms MenuStrip
Máte-li aplikaci MDI (Multiple Document Interface), můžete sloučit položky nabídky nebo celé nabídky z podřízeného formuláře do nabídek nadřazeného formuláře.  
  
 Toto téma popisuje základní koncepty spojené s slučováním položek nabídky v aplikaci MDI.  
  
## <a name="general-concepts"></a>Obecné koncepty  
 Sloučení procedur zahrnuje cíl i správu zdrojového kódu:  
  
- Cílem je ovládací prvek <xref:System.Windows.Forms.MenuStrip> v nadřazeném nebo nadřazeném formuláři MDI, do kterého slučujete položky nabídky.  
  
- Zdroj je ovládací prvek <xref:System.Windows.Forms.MenuStrip> v podřízeném formuláři MDI, který obsahuje položky nabídky, které chcete sloučit do cílové nabídky.  
  
 Vlastnost <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> identifikuje položku nabídky, jejíž rozevírací seznam se naplní názvy aktuálních podřízených objektů MDI nadřazeného formuláře MDI. Například obvykle vypíšete podřízené položky MDI, které jsou aktuálně otevřeny v nabídce **okna** .  
  
 Vlastnost <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> určuje, které položky nabídky pocházejí z <xref:System.Windows.Forms.MenuStrip> v podřízeném formuláři MDI.  
  
 Položky nabídky můžete sloučit ručně nebo automaticky. Položky nabídky se sloučí stejným způsobem jak u obou metod, ale sloučení se aktivuje odlišně, jak je popsáno v části Ruční sloučení a automatické slučování dále v tomto tématu. V ručním i automatickém sloučení má každá akce sloučení vliv na další akci sloučení.  
  
 <xref:System.Windows.Forms.MenuStrip> slučuje položky nabídky z jednoho <xref:System.Windows.Forms.ToolStrip> na jinou namísto klonování, stejně jako v případě <xref:System.Windows.Forms.MainMenu>.  
  
## <a name="mergeaction-values"></a>Hodnoty MergeAction  
 Akci sloučení pro položky nabídky ve zdrojovém <xref:System.Windows.Forms.MenuStrip> nastavíte pomocí vlastnosti <xref:System.Windows.Forms.MergeAction>.  
  
 Následující tabulka popisuje význam a typické použití dostupných akcí sloučení.  
  
|Hodnota MergeAction|Popis|Typické použití|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|Výchozí Přidá zdrojovou položku na konec kolekce cílové položky.|Přidání položek nabídky na konec nabídky, je-li některá část programu aktivována.|  
|<xref:System.Windows.Forms.MergeAction.Insert>|Přidá zdrojovou položku do kolekce cílové položky v umístění určeném vlastností <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> nastavenou na zdrojové položce.|Přidání položek nabídky do středu nebo začátek nabídky, je-li některá část programu aktivována.<br /><br /> Pokud je hodnota <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> pro obě položky nabídky stejná, budou přidány v obráceném pořadí. Nastavte <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> odpovídajícím způsobem zachovat původní pořadí.|  
|<xref:System.Windows.Forms.MergeAction.Replace>|Vyhledá shodu textu nebo použije <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud není nalezena shoda textu, a poté nahradí odpovídající položku cílové nabídky položkou nabídky zdroje.|Výměna položky cílové nabídky se zdrojovou položkou nabídky se stejným názvem, která má něco jiného.|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|Vyhledá shodu textu nebo použije <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud není nalezena shoda textu, a pak přidá všechny rozevírací nabídky ze zdroje do cíle.|Vytvoření struktury nabídky, která vloží nebo přidá položky nabídky do podnabídky nebo odebere položky nabídky z podnabídky. Například můžete přidat položku nabídky z podřízeného objektu MDI do hlavní nabídky <xref:System.Windows.Forms.MenuStrip>**Uložit jako** .<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> umožňuje procházet strukturu nabídky bez provedení jakékoli akce. Poskytuje způsob, jak vyhodnotit následné položky.|  
|<xref:System.Windows.Forms.MergeAction.Remove>|Vyhledá shodu textu nebo použije <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> hodnotu, pokud se nenajde shoda textu, a pak položku z cíle odebere.|Odebrání položky nabídky z cílového <xref:System.Windows.Forms.MenuStrip>.|  
  
## <a name="manual-merging"></a>Ruční sloučení  
 Automatické sloučení se účastní jenom <xref:System.Windows.Forms.MenuStrip>ch ovládacích prvků. Pro kombinování položek jiných ovládacích prvků, například <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky je nutné je sloučit ručně, voláním <xref:System.Windows.Forms.ToolStripManager.Merge%2A> a <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> metod v kódu podle potřeby.  
  
## <a name="automatic-merging"></a>Automatické slučování  
 Automatické slučování pro aplikace MDI lze použít aktivací zdrojového formuláře. Chcete-li použít <xref:System.Windows.Forms.MenuStrip> v aplikaci MDI, nastavte vlastnost <xref:System.Windows.Forms.Form.MainMenuStrip%2A> na cílový <xref:System.Windows.Forms.MenuStrip> tak, aby se akce sloučení provedené na zdrojovém <xref:System.Windows.Forms.MenuStrip> projevily v cílovém <xref:System.Windows.Forms.MenuStrip>.  
  
 Automatické slučování můžete aktivovat aktivací <xref:System.Windows.Forms.MenuStrip> ve zdroji MDI. Při aktivaci se zdrojový <xref:System.Windows.Forms.MenuStrip> sloučí do cíle MDI. Když se nový formulář stane aktivní, sloučení se vrátí v posledním formuláři a aktivuje se v novém formuláři. Toto chování můžete řídit nastavením vlastnosti <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> podle potřeby u každého <xref:System.Windows.Forms.ToolStripItem>a nastavením vlastnosti <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> u každého <xref:System.Windows.Forms.MenuStrip>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.MenuStrip>
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
- [Postupy: Vytvoření seznamu okna MDI pomocí MenuStrip](how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)
- [Postupy: Nastavení automatického slučování nabídek pro aplikace MDI](how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
