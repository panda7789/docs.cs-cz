---
title: Souhrn technologie ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], technology summary
- status bars [Windows Forms], technology summary
- toolbars [Windows Forms], technology summary
- menus [Windows Forms], technology summary
ms.assetid: e8d61973-7af9-429f-9df5-05a899c15a7b
ms.openlocfilehash: 26317fad5796989a58a48e4f26549805b279228a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288147"
---
# <a name="toolstrip-technology-summary"></a>Souhrn technologie ToolStrip
Toto téma shrnuje informace o `ToolStrip` ovládacího prvku a tříd, které podporují jeho použití.  
  
 `ToolStrip` Ovládacího prvku a jeho přidružených tříd vzniklo kompletní řešení pro vytváření panelů nástrojů, stavovém řádku a nabídky.  
  
## <a name="namespaces"></a>Jmenné prostory  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="background"></a>Pozadí  
 S `ToolStrip` ovládacího prvku a jeho přidružených tříd, můžete vytvořit funkce pokročilých nástrojů, které je konzistentní a profesionální vzhled a chování. `ToolStrip` Ovládacího prvku a třídy nabídnout následující vylepšení oproti předchozí ovládací prvky:  
  
-   Konzistentní model událostí.  
  
-   Konzistentní chování návrhu, který obsahuje seznamy úkolů a editory kolekce položek.  
  
-   Vlastní vykreslování s `ToolStripManager` a `ToolStripRenderer`.  
  
-   Předdefinované rafting (vodorovně nebo svisle mezeru v oblasti nástroje, pokud je ukotven sdílení) se `ToolStripContainer` a `ToolStripPanel`.  
  
-   Doby návrhu a běhu změny pořadí položek s <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> vlastnost.  
  
-   Přemístění do nabídky přetečení s položkami <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> vlastnost.  
  
-   Umístění zcela konfigurovat ovládací prvek `ToolStripContainer`, `ToolStripPanel`, a `ToolStripContentPanel`.  
  
-   Hostování `ToolStrip`, tradiční nebo vlastních ovládacích prvků pomocí `ToolStripControlHost`.  
  
-   Slučování `ToolStrip` ovládací prvky pomocí `ToolStripPanel`.  
  
 `ToolStrip` je rozšiřitelný základní třída pro `MenuStrip`, `ContextMenuStrip`, a `StatusStrip`. Tyto ovládací prvky jsou <xref:System.Windows.Forms.ToolStripItem> kontejnery, které dědí běžné chování a zpracování událostí, rozšířená tak, aby každá implementace se zabývá chování, která je vhodná pro něj. Ovládací prvky, které jsou odvozeny z <xref:System.Windows.Forms.ToolStripItem> jsou uvedeny v následující tabulce. Základní `ToolStrip` třída zpracovává Malování, vstup uživatele a události a přetažení pro tyto ovládací prvky.  
  
 `ToolStrip`, `MenuStrip`, `ContextMenuStrip`, A `StatusStrip` ovládací prvky nahradit předchozí nástrojů, nabídky, nabídku a ovládací prvky stavového řádku, i když tyto ovládací prvky se zachovává kvůli zpětné kompatibilitě.  
  
## <a name="toolstrip-classes-at-a-glance"></a>Ovládací prvek ToolStrip třídy na první pohled  
 Následující tabulka uvádí třídy ovládacího prvku ToolStrip seskupené podle technologickou oblast.  
  
|Technologickou oblast|Třída|  
|---------------------|-----------|  
|Panel nástrojů, nabídek a stav kontejnerů|<xref:System.Windows.Forms.ToolStrip><br /><br /> <xref:System.Windows.Forms.MenuStrip><br /><br /> <xref:System.Windows.Forms.ContextMenuStrip><br /><br /> <xref:System.Windows.Forms.StatusStrip><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownMenu>|  
|Položek ToolStrip|<xref:System.Windows.Forms.ToolStripLabel><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownItem><br /><br /> <xref:System.Windows.Forms.ToolStripMenuItem><br /><br /> <xref:System.Windows.Forms.ToolStripButton><br /><br /> <xref:System.Windows.Forms.ToolStripStatusLabel><br /><br /> <xref:System.Windows.Forms.ToolStripSeparator><br /><br /> <xref:System.Windows.Forms.ToolStripControlHost><br /><br /> <xref:System.Windows.Forms.ToolStripComboBox><br /><br /> <xref:System.Windows.Forms.ToolStripTextBox><br /><br /> <xref:System.Windows.Forms.ToolStripProgressBar><br /><br /> <xref:System.Windows.Forms.ToolStripDropDownButton><br /><br /> <xref:System.Windows.Forms.ToolStripSplitButton>|  
|Umístění|<xref:System.Windows.Forms.ToolStripContainer><br /><br /> <xref:System.Windows.Forms.ToolStripContentPanel><br /><br /> <xref:System.Windows.Forms.ToolStripPanel>|  
|Prezentace a vykreslování|<xref:System.Windows.Forms.ToolStripManager><br /><br /> <xref:System.Windows.Forms.ToolStripRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripProfessionalRenderer><br /><br /> <xref:System.Windows.Forms.ToolStripRenderMode><br /><br /> <xref:System.Windows.Forms.ToolStripManagerRenderMode>|  
  
## <a name="toolstrip-design-time-features"></a>Funkce ovládacího prvku ToolStrip návrhu  
 <xref:System.Windows.Forms.ToolStrip> Řadu ovládacích prvků poskytuje bohatou sadu nástrojů a šablon pro místní úpravy a definování foundation uživatelského rozhraní tak, že můžete rychle vytvořit fungující aplikaci.  
  
### <a name="task-dialog-boxes"></a>Dialogová okna úloh  
 V sadě Visual Studio kliknutím na inteligentní značku na ovládací prvek v návrháři, zobrazí se seznam úloh pro pohodlný přístup mnoha často používané příkazy.  
  
-   [MenuStrip – dialogové okno úloh](https://msdn.microsoft.com/library/ms233645\(v=vs.110\))  
  
-   [ToolStrip – dialogové okno úloh](https://msdn.microsoft.com/library/ms233648\(v=vs.110\))  
  
-   [ContextMenuStrip – dialogové okno úloh](https://msdn.microsoft.com/library/ms233646\(v=vs.110\))  
  
-   [StatusStrip – dialogové okno úloh](https://msdn.microsoft.com/library/ms233642\(v=vs.110\))  
  
-   [ToolStripContainer – dialogové okno úloh](https://msdn.microsoft.com/library/ms233647\(v=vs.110\))  
  
### <a name="items-collection-editors"></a>Editory kolekce položek  
 V sadě Visual Studio, po kliknutí na **upravit položky** úlohy seznamu nebo klikněte pravým tlačítkem na ovládací prvek a vyberte **upravit položky** v místní nabídce, zobrazí se editor kolekce pro ovládací prvek. Editory kolekce umožňují přidat, odebrat a změnit pořadí položek, které obsahuje ovládací prvek. Můžete také zobrazit a změnit vlastnosti ovládacího prvku a ovládacího prvku položek.  
  
-   [MenuStrip – Editor kolekce položek](https://msdn.microsoft.com/library/ms233625\(v=vs.110\))  
  
-   [StatusStrip – Editor kolekce položek](https://msdn.microsoft.com/library/ms233631\(v=vs.110\))  
  
-   [ContextMenuStrip – Editor kolekce položek](https://msdn.microsoft.com/library/ms233641\(v=vs.110\))  
  
-   [Editor kolekce položek ovládacího prvku ToolStrip](https://msdn.microsoft.com/library/ms233643\(v=vs.110\))  
  
## <a name="hosting-controls"></a>Hostování ovládacích prvků  
 <xref:System.Windows.Forms.ToolStripControlHost> Třída poskytuje integrované obálky pro <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, a <xref:System.Windows.Forms.ToolStripProgressBar> ovládací prvky. Můžete také uložit žádné další existující nebo ovládacího prvku COM v <xref:System.Windows.Forms.ToolStripControlHost>.  
  
 Příklad hostování ovládacího prvku, naleznete v tématu [postupy: zabalení ovládacího prvku Windows Forms pomocí ToolStripControlHost](../../../../docs/framework/winforms/controls/how-to-wrap-a-windows-forms-control-with-toolstripcontrolhost.md).  
  
## <a name="rendering"></a>vykreslování  
 <xref:System.Windows.Forms.ToolStrip> třídy implementovat vykreslování schéma, které se značně liší od jiných ovládacích prvků Windows Forms. Toto schéma snadno použít styly a motivů.  
  
 Použít styl <xref:System.Windows.Forms.ToolStrip> a všechny <xref:System.Windows.Forms.ToolStripItem> objekty, které obsahuje, není nutné ke zpracování <xref:System.Windows.Forms.ToolStripItem.Paint> událost pro každou položku. Místo toho můžete nastavit <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> vlastnost na jednu z <xref:System.Windows.Forms.ToolStripRenderMode> hodnoty jiné než <xref:System.Windows.Forms.ToolStripRenderMode.Custom>. Alternativně můžete nastavit <xref:System.Windows.Forms.ToolStrip.Renderer%2A> přímo na všechny třídy, která dědí z <xref:System.Windows.Forms.ToolStripRenderer> třídy. Nastavení této vlastnosti automaticky nastaví <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>.  
  
 Můžete provést stejný styl u více <xref:System.Windows.Forms.ToolStrip> objekty ve stejné aplikaci tak, že nastavíte <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> k <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode> a nastavení <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A> nebo <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> vlastnost <xref:System.Windows.Forms.ToolStripManagerRenderMode> , který chcete nebo <xref:System.Windows.Forms.ToolStripRenderer> hodnotu, v uvedeném pořadí.  
  
 Příklady vykreslování, najdete v článku [postupy: vytvoření a nastavení vlastního Rendereru pro ovládací prvek ToolStrip ve Windows Forms](../../../../docs/framework/winforms/controls/create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md).  
  
## <a name="styles-and-themes"></a>Styly a motivů  
 <xref:System.Windows.Forms.ToolStrip> a přidružených tříd poskytují snadný způsob, jak podporují vizuální styly a vlastní vzhled, které nevyžadují žádné přepisování <xref:System.Windows.Forms.ToolStripItem.OnPaint%2A> metod pro každou položku. Použití <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> a <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> a <xref:System.Windows.Forms.ToolStrip.Renderer%2A> vlastnosti.  
  
## <a name="rafting-and-docking"></a>Rafting a ukotvení  
 Můžete raft, ukotvit nebo absolutní pozice <xref:System.Windows.Forms.ToolStrip> ovládacích prvků. <xref:System.Windows.Forms.ToolStrip> položky jsou rozloženy modulem <xref:System.Windows.Forms.ToolStrip.LayoutEngine%2A> kontejneru.  
  
 *Rafting* je možnost sdílet místa na vodorovné nebo svislé panely nástrojů. Formuláře Windows může mít <xref:System.Windows.Forms.ToolStripContainer> , která naopak má panely na levé straně formuláře, pravé, horní a dolní strana pro umístění a rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky. Více <xref:System.Windows.Forms.ToolStrip> ovládací prvky zásobníku svisle, pokud je vložíte do doleva nebo doprava <xref:System.Windows.Forms.ToolStripContainer>. Jejich řadily vodorovně, pokud je umístíte v horní nebo dolní <xref:System.Windows.Forms.ToolStripContainer>. Můžete použít centrální <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> na pozici tradiční ovládací prvky ve formuláři.  
  
 Některé nebo všechny <xref:System.Windows.Forms.ToolStripContainer> ovládací prvky jsou přímo vybrat v době návrhu a můžete je odstranit. A <xref:System.Windows.Forms.ToolStripContainer> je rozšiřitelná a sbalitelný a mění svou velikost ovládacích prvků, které obsahuje.  
  
 *Ukotvení* je určení jednoduché umístění ovládacího prvku na vlevo, vpravo, horní nebo dolní strana formuláře.  
  
 Výhodou rafting přes ukotvení je, že <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.StatusStrip> ovládací prvky můžete sdílet místa na vodorovné nebo svislé s jinými ovládacími prvky.  
  
 Většina <xref:System.Windows.Forms.ToolStrip> ovládací prvky lze ukotvit do formuláře jako ostatní ovládací prvky namísto použití rafting. Můžete také určit, že <xref:System.Windows.Forms.ToolStrip> ovládací prvek volně umístit na formuláři tak, že odeberete z jeho <xref:System.Windows.Forms.ToolStripContainer> a nastavení jeho `Dock` vlastnost `None`, nebo můžete zadat absolutní pozici nastavením funkcím <xref:System.Windows.Forms.Control.Location%2A> Vlastnost. Zobrazit [postupy: Přesunutí ToolStrip mimo prvek ToolStripContainer formuláře](../../../../docs/framework/winforms/controls/how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form.md).  
  
 Použití jednoho nebo více <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky pro větší flexibilitu, hlavně pro aplikace rozhraní více dokumentů (MDI), nebo pokud není nutné <xref:System.Windows.Forms.ToolStripContainer>. A <xref:System.Windows.Forms.ToolStripPanel> ukotvitelné místo pro vyhledání a rafting <xref:System.Windows.Forms.ToolStrip> ovládacích prvků, ale ne tradiční ovládací prvky. Ve výchozím nastavení <xref:System.Windows.Forms.ToolStripPanel> se nezobrazí v návrháři **nástrojů**, ale můžete ji existuje kliknutím pravým tlačítkem myši **nástrojů**a potom klikněte na tlačítko **zvolit položky**. Můžete také programově přistupovat <xref:System.Windows.Forms.ToolStripPanel> jako jakékoli jiné třídy.  
  
 <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, A <xref:System.Windows.Forms.StatusStrip> nechat položky přetečení. To se podobá způsobu, jakým tyto položky se chovají na panely nástrojů Microsoft Office.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)
