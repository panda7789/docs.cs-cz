---
title: Souhrn technologie ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: c4f7b13590457623bbdfd6e4c07317f3a0285fd0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541908"
---
# <a name="toolstrip-technology-summary"></a>Souhrn technologie ToolStrip
Toto téma shrnuje informace o `ToolStrip` řízení a třídy, které podporují jeho použití.  
  
 `ToolStrip` Ovládací prvek a jeho přidružené třídy poskytují kompletní řešení pro vytváření panelů nástrojů, stavové řádky a nabídek.  
  
## <a name="namespaces"></a>Jmenné prostory  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Pozadí  
 Pomocí `ToolStrip` ovládací prvek a jeho přidružené třídy, můžete vytvořit na panelu nástrojů Upřesnit funkce, která je konzistentní a profesionální vzhled a chování. `ToolStrip` Řízení a třídy nabízejí následující vylepšení přes předchozí ovládací prvky:  
  
-   Více konzistentní model událostí.  
  
-   Více konzistentní chování návrhu, které obsahuje seznam úloh a editory kolekce položky.  
  
-   Vlastní vykreslení s `ToolStripManager` a `ToolStripRenderer`.  
  
-   Integrované s rafting (sdílení vodorovné nebo svislé prostor v rámci oblasti nástroje, pokud je ukotveno) `ToolStripContainer` a `ToolStripPanel`.  
  
-   Návrh a spuštění změny pořadí položek s <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost.  
  
-   Přemístění položky nabídky přetečení s <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost.  
  
-   Umístění úplně konfigurovat ovládací prvek `ToolStripContainer`, `ToolStripPanel`, a `ToolStripContentPanel`.  
  
-   Hostování `ToolStrip`, tradiční nebo vlastních ovládacích prvků pomocí `ToolStripControlHost`.  
  
-   Sloučení `ToolStrip` ovládací prvky pomocí `ToolStripPanel`.  
  
 `ToolStrip` je rozšiřitelný základní třídu pro `MenuStrip`, `ContextMenuStrip`, a `StatusStrip`. Tyto ovládací prvky jsou <xref:System.Windows.Forms.ToolStripItem> kontejnery, které dědí společné chování a zpracování událostí rozšířit tak, aby každý implementace zabývá chování, která je vhodná pro ni. Ovládací prvky, které jsou odvozeny od <xref:System.Windows.Forms.ToolStripItem> jsou uvedeny v následující tabulce. Základní `ToolStrip` třída zpracovává Malování, vstup uživatele a přetažení myší události pro tyto ovládací prvky.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, A `StatusStrip` ovládací prvky nahradit předchozí nástrojů nabídky, místní nabídky a ovládací prvky stavového řádku, i když tyto ovládací prvky se zachovává kvůli zpětné kompatibilitě.  
  
## <a name="toolstrip-classes-at-a-glance"></a>ToolStrip – třídy na první pohled  
 V následující tabulce jsou seskupené podle oblast technologie ToolStrip třídy.  
  
|Oblast technologie|Třída|  
|---------------------|-----------|  
|Panel nástrojů, stavu a nabídky kontejnery|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Položek ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Umístění|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Prezentační a vykreslování|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>ToolStrip – návrh funkce  
 <xref:System.Windows.Forms.ToolStrip> Řadu ovládacích prvků pro úpravy a definování základ pro uživatelské rozhraní, takže můžete rychle vytvořit funkční aplikaci na místě poskytuje bohatou sadu nástrojů a šablony.  
  
### <a name="task-dialog-boxes"></a>Dialogová okna úloh  
 V sadě Visual Studio kliknutím na inteligentní značku ovládacího prvku v návrháři, zobrazí se seznam úloh pro pohodlný přístup mnoho často používané příkazy.  
  
-   [Dialogové okno úloh MenuStrip](http://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [Dialogové okno úloh ToolStrip](http://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [Dialogové okno úloh ContextMenuStrip](http://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [Dialogové okno úloh StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [Dialogové okno úloh ToolStripContainer](http://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Editory kolekce položek  
 V sadě Visual Studio, po kliknutí na tlačítko **upravit položky** v úloze seznamu nebo klikněte pravým tlačítkem na ovládací prvek a vyberte **upravit položky** v místní nabídce se zobrazí editor kolekce pro ovládací prvek. Editory kolekce umožňují přidání, odebrání a změna pořadí položek, které obsahuje ovládací prvek. Můžete také zobrazit a změnit vlastnosti pro ovládací prvek a položek ovládacího prvku.  
  
-   [Editor kolekce položek MenuStrip](http://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [Editor kolekce položek StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [Editor kolekce položek ContextMenuStrip](http://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [Editor kolekce položek ToolStrip](http://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Hostování ovládacích prvků  
 <xref:System.Windows.Forms.ToolStripControlHost> Třída poskytuje integrované obálek pro <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky. Můžete také hostovat další existující nebo ovládacího prvku COM <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Příklad – hostování ovládacího prvku, naleznete v části [postupy: zalomení ovládacího prvku Windows Forms pomocí ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>Vykreslování  
 <xref:System.Windows.Forms.ToolStrip> třídy implementovat vykreslování schéma, které se významně liší od jiných ovládacích prvků Windows Forms. Toto schéma snadno použít styly a motivů.  
  
 Chcete-li použít styl pro <xref:System.Windows.Forms.ToolStrip> a všechny <xref:System.Windows.Forms.ToolStripItem> objekty, které obsahuje, není nutné pro zpracování <xref:System.Windows.Forms.ToolStripItem.Paint> událost pro každou položku. Místo toho můžete nastavit <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost na jednu z <xref:System.Windows.Forms.ToolStripRenderMode> hodnoty jiné než <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternativně můžete nastavit <xref:System.Windows.Forms.ToolStrip.Renderer%2A> přímo na všechny třídy, která dědí z <xref:System.Windows.Forms.ToolStripRenderer> třídy. Nastavení této vlastnosti se automaticky nastaví <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Můžete použít stejný styl pro více <xref:System.Windows.Forms.ToolStrip> objekty ve stejné aplikaci, a to nastavením <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> k <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> a nastavení <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> vlastnost <xref:System.Windows.Forms.ToolStripManagerRenderMode> , které chcete nebo <xref:System.Windows.Forms.ToolStripRenderer> hodnotu, v uvedeném pořadí.  
  
 Příklady vykreslování najdete v tématu [postupy: vytvoření a nastavení vlastní vykreslení ovládacího prvku ToolStrip ve Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Styly a motivů  
 <xref:System.Windows.Forms.ToolStrip> a související třídy poskytují snadný způsob, jak podporují vizuální styly a vlastní vzhled, které nevyžadují přepsání <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> metody pro každou položku. Použití <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> a <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnosti.  
  
## <a name="rafting-and-docking"></a>Rafting a dokování  
 Můžete raft, ukotvení nebo absolutní pozice <xref:System.Windows.Forms.ToolStrip> ovládací prvky. <xref:System.Windows.Forms.ToolStrip> položky jsou nastíněny <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kontejneru.  
  
 *Rafting* je schopnost panely nástrojů sdílet místo vodorovně nebo svisle. Může mít formuláři Windows <xref:System.Windows.Forms.ToolStripContainer> která naopak má panelů na formuláře levé, pravé, horní a dolní straně pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky. Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku ve svislém směru, pokud jejich umístění v doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>. Pokud je uvést do pravého horního nebo dolního jejich vodorovně zásobníku <xref:System.Windows.Forms.ToolStripContainer>. Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky na formuláři.  
  
 Kterékoli nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit. A <xref:System.Windows.Forms.ToolStripContainer> je rozšíření a sbalitelné a změní velikost s ovládacími prvky, které obsahuje.  
  
 *Ukotvení* je zadání jednoduchého umístění ovládacího prvku na levé, pravé, horní nebo dolní straně formuláře.  
  
 Výhodou rafting přes ukotvení je, že <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky můžete sdílet vodorovné nebo svislé místa s dalšími kontrolami.  
  
 Většina <xref:System.Windows.Forms.ToolStrip> ovládací prvky lze ukotvit do formuláře jako ostatní ovládací prvky místo použití rafting. Můžete také určit, že <xref:System.Windows.Forms.ToolStrip> být odebráním z volně umístěný ovládací prvek na formuláři jeho <xref:System.Windows.Forms.ToolStripContainer> a nastavení jeho `Dock` vlastnost `None`, nebo můžete zadat absolutní pozici nastavením příslušné <xref:System.Windows.Forms.Control.Location%2A> Vlastnost. V tématu [postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Používat jednu nebo více <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky pro větší flexibilitu, zejména pro aplikace rozhraní více dokumentů (MDI), nebo pokud není nutné <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> lze ukotvit místo pro vyhledání a rafting <xref:System.Windows.Forms.ToolStrip> ovládací prvky, ale není tradiční ovládací prvky. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStripPanel> nezobrazí v návrháři **sada nástrojů**, ale můžete ji existuje kliknutím pravým tlačítkem myši **sada nástrojů**a pak klikněte na **zvolit položky**. Můžete také programově přistupovat <xref:System.Windows.Forms.ToolStripPanel> jako jiná třída.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, A <xref:System.Windows.Forms.StatusStrip> umožní položky přetečení. Toto je podobným způsobem, který tyto položky chovat na panely nástrojů Microsoft Office.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
