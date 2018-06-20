---
title: Obousměrná podpora pro formulářové aplikace Windows
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbe14e6c05fd6ef155b564e499157e00c5d809e5
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208445"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Obousměrná podpora pro formulářové aplikace Windows
Visual Studio můžete použít k vytvoření aplikace pro systém Windows podporující obousměrných jazycích (vpravo zprava doleva) jako je například arabština a hebrejština. To zahrnuje standardní formulářů, dialogová okna, MDI formuláře a všechny ovládací prvky můžete pracovat v tyto formuláře – to znamená, že všechny objekty v <xref:System.Windows.Forms.Control> oboru názvů.  
  
## <a name="culture-support"></a>Podpora jazykovou verzi  
 Nastavení jazykové verze uživatelského rozhraní a jazykovou verzi určit, jak funguje aplikace s daty, časy, měny a další informace. Podporu pro jazykovou verzi a jazyková verze uživatelského rozhraní je stejný pro obousměrné jazyky, jako je pro jiné jazyky.   Viz také [třídy specifické pro jazykovou verzi pro globální formuláře systému Windows a webové formuláře](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.110\)) nebo [třídy specifické pro jazykovou verzi pro globální formuláře systému Windows a webové formuláře](http://msdn.microsoft.com/library/94ye9x8c\(v=vs.120\))  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft a RightToLeftLayout vlastnosti  
 Základní <xref:System.Windows.Forms.Control> zahrnuje třídy, ze které jsou odvozeny formulářů, <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost, kterou můžete nastavit, chcete-li změnit pořadí čtení formuláře a jeho ovládacích prvků. Pokud nastavíte formuláře <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost, ve výchozím nastavení ovládacích prvků formuláře dědí toto nastavení. Ale můžete také nastavit <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost jednotlivě na většinu ovládacích prvků. Viz také [postupy: zobrazení zprava doleva Text ve Windows Forms pro globalizaci](http://msdn.microsoft.com/library/7d3337xw\(v=vs.110\)).  
  
 Účinek <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost se může lišit od jeden prvek do jiného. V některé ovládací prvky vlastnost pouze nastaví pořadí čtení jako v <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ToolTip> ovládací prvky. V jiných ovládacích prvků <xref:System.Windows.Forms.Control.RightToLeft%2A> změny vlastností pořadí čtení a rozložení. To zahrnuje <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.CheckBox> ovládací prvky. Další ovládací prvky vyžadovat, aby <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastnost použijí pro zrcadlení jeho rozložení zprava doleva. Následující tabulka poskytuje podrobné informace o tom, jak je <xref:System.Windows.Forms.Control.RightToLeft%2A> a <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastností na jednotlivých ovládacích prvků Windows Forms.  
  
|Ovládací prvek nebo součást|Účinek vlastnosti RightToLeft|Účinek vlastnosti RightToLeftLayout|Vyžaduje zrcadlení?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Nastaví RTL pořadí čtení. Obrátí <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, a <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Neplatí|Ne|  
|<xref:System.Windows.Forms.CheckBox>|Zaškrtávací políčko se zobrazí na pravé straně textu|Neplatí|Ne|  
|<xref:System.Windows.Forms.CheckedListBox>|Všechna zaškrtávací políčka se zobrazí na pravé straně textu|Neplatí|Ne|  
|<xref:System.Windows.Forms.ColorDialog>|Není vliv; závisí na jazyce operačního systému|Neplatí|Ne|  
|<xref:System.Windows.Forms.ComboBox>|Položky v ovládacím prvku pole se seznamem jsou zarovnaný doprava|Neplatí|Ne|  
|<xref:System.Windows.Forms.ContextMenu>|Zobrazí se vpravo zarovnaný s pořadí čtení zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.DataGrid>|Zobrazí se vpravo zarovnaný s pořadí čtení zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.DataGridView>|Ovlivňuje i pořadí a řízení rozložení pro čtení zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.DateTimePicker>|Není vliv; závisí na jazyce operačního systému|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.DomainUpDown>|Vlevo zarovná nahoru a dolů|Neplatí|Ne|  
|<xref:System.Windows.Forms.ErrorProvider>|Nepodporováno|Neplatí|Ne|  
|<xref:System.Windows.Forms.FontDialog>|Závisí na jazyce operačního systému|Neplatí|Ne|  
|<xref:System.Windows.Forms.Form>|Nastaví pořadí čtení zprava doleva a obrátí posuvníky|Odpovídá formuláře|Ano|  
|<xref:System.Windows.Forms.GroupBox>|Popisek se zobrazí vpravo zarovnaný. Podřízené ovládací prvky mohou dědit tuto vlastnost.|Použití <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku zprava doleva zrcadlení pro podporu|Ne|  
|<xref:System.Windows.Forms.HScrollBar>|Začíná posouvací políčko (Flash) zarovnaný doprava|Neplatí|Ne|  
|<xref:System.Windows.Forms.ImageList>|Není požadováno|Neplatí|Ne|  
|<xref:System.Windows.Forms.Label>|Zobrazí zarovnaný doprava. Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Neplatí|Ne|  
|<xref:System.Windows.Forms.LinkLabel>|Zobrazí zarovnaný doprava. Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Neplatí|Ne|  
|<xref:System.Windows.Forms.ListBox>|Položky jsou zarovnaný doprava|Neplatí|Ne|  
|<xref:System.Windows.Forms.ListView>|Nastaví pořadí čtení zprava doleva; elementy zůstat zarovnaný doleva|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.MainMenu>|Zobrazí vpravo zarovnaný RTL pořadí čtení v době běhu (ne v době návrhu)|Neplatí|Ne|  
|<xref:System.Windows.Forms.MaskedTextBox>|Zobrazí text zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.MonthCalendar>|Není vliv; závisí na jazyce operačního systému|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.NotifyIcon>|Nepodporováno|Nepodporováno|Ne|  
|<xref:System.Windows.Forms.NumericUpDown>|Tlačítka nahoru a dolů jsou zarovnaný doleva|Neplatí|Ne|  
|<xref:System.Windows.Forms.OpenFileDialog>|V operačních systémech zprava doleva, nastavení obsahující formulář <xref:System.Windows.Forms.Control.RightToLeft> vlastnost <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizováno dialogové okno |Neplatí|Ne|  
|<xref:System.Windows.Forms.PageSetupDialog>|Není vliv; závisí na jazyce operačního systému|Neplatí|Ne|  
|<xref:System.Windows.Forms.Panel>|Podřízené ovládací prvky mohou dědit tato vlastnost|Použití <xref:System.Windows.Forms.TableLayoutPanel> v ovládacím prvku pro práva k levé podpory|Ano|  
|<xref:System.Windows.Forms.PictureBox>|Nepodporováno|Neplatí|Ne|  
|<xref:System.Windows.Forms.PrintDialog>|Není vliv; závisí na jazyce operačního systému|Neplatí|Ne|  
|<xref:System.Drawing.Printing.PrintDocument>|Svislý posuvník stát zarovnaný doleva a vodorovného posuvníku spustí vlevo|Neplatí|Ne|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nepodporováno|Nepodporováno|Ne|  
|<xref:System.Windows.Forms.ProgressBar>|Tato vlastnost vliv|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.RadioButton>|Přepínač se zobrazí na pravé straně textu|Neplatí|Ne|  
|<xref:System.Windows.Forms.RichTextBox>|Ovládací prvky, které zahrnují text se zobrazí zprava doleva s pořadí čtení zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.SaveFileDialog>|Není vliv; závisí na jazyce operačního systému|Neplatí|Ne|  
|<xref:System.Windows.Forms.SplitContainer>|Rozložení panelu je obrácený; svislý posuvník se zobrazí na levé straně; Vodorovný posuvník začíná zprava|Použití <xref:System.Windows.Forms.TableLayoutPanel> k zrcadlení pořadí podřízených ovládacích prvků|Ne|  
|<xref:System.Windows.Forms.Splitter>|Nepodporováno|Neplatí|Ne|  
|<xref:System.Windows.Forms.StatusBar>|Nepodporuje; použít <xref:System.Windows.Forms.StatusStrip> místo|Neplatí; použít <xref:System.Windows.Forms.StatusStrip> místo|Ne|  
|<xref:System.Windows.Forms.TabControl>|Není ovlivněna touto vlastností|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.TextBox>|Zobrazí text zprava doleva s pořadí čtení zprava doleva.|Neplatí|Ne|  
|<xref:System.Windows.Forms.Timer>|Není požadováno|Není požadováno|Ne|  
|<xref:System.Windows.Forms.ToolBar>|Není ovlivněna touto vlastností; použít <xref:System.Windows.Forms.ToolStrip> místo|Neplatí; použít <xref:System.Windows.Forms.ToolStrip> místo|Ano|  
|<xref:System.Windows.Forms.ToolTip>|Nastaví RTL pořadí čtení|Neplatí|Ne|  
|<xref:System.Windows.Forms.TrackBar>|Posuv nebo sledovat začíná zprava; Když <xref:System.Windows.Forms.TrackBar.Orientation%2A> je svislý, dojde k rysky vpravo|Neplatí|Ne|  
|<xref:System.Windows.Forms.TreeView>|Nastaví RTL pořadí pouze pro čtení|Odpovídá ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.UserControl>|Svislý posuvník se zobrazí na levé straně; Vodorovný posuvník má jezdec na pravé straně|Žádné přímé podpory; použít <xref:System.Windows.Forms.TableLayoutPanel>|Ne|  
|<xref:System.Windows.Forms.VScrollBar>|Zobrazí na levé straně místo pravé straně posouvatelného ovládacích prvků|Neplatí|Ne|  
  
## <a name="encoding"></a>Kódování  
 Windows Forms – Podpora kódování Unicode, můžete použít libovolný znak nastavit při vytváření aplikace obousměrná. Ne všechny ovládací prvky Windows Forms však podporují kódování Unicode na všech platformách. Další informace najdete v tématu [kódování a globalizace Windows Forms](../../../../docs/framework/winforms/advanced/encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení textu pomocí pořadí čtení zprava doleva. <xref:System.Drawing.Graphics.DrawString%2A> Podporuje metodu, která slouží k vykreslení textu `StringFormat` parametr, který můžete nastavit, aby <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> členem <xref:System.Drawing.StringFormatFlags> výčtu, aby bylo možné obrátit bod pro text.  
  
## <a name="common-dialog-boxes"></a>Společná dialogová okna  
 Systémové nástroje, jako je například dialogové okno otevřít soubor se řídí služby systému Windows. Jazykové elementy dědí z operačního systému. Pokud používáte verzi systému Windows s nastavením správný jazyk, budou tyto dialogy fungovat správně s obousměrných jazycích.  
  
 Okna zpráv podobně projít operačního systému a podporují obousměrný text. Titulky tlačítek pole zprávy jsou založené na aktuální nastavení jazyka. Ve výchozím nastavení okna zpráv nepoužívejte čtení zprava doleva pořadí, ale můžete zadat parametr Chcete-li změnit pořadí čtení při zobrazení okna zpráv.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft posuvníky a ovládací prvek ScrollableControl  
 V současné době není omezení ve Windows Forms, který brání všechny třídy odvozené od <xref:System.Windows.Forms.ScrollableControl> z funguje správně při obě <xref:System.Windows.Forms.Control.RightToLeft%2A> je povolená a <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> je nastaven na <xref:System.Windows.Forms.RightToLeft.Yes>. Předpokládejme například, že umístěte ovládací prvek, jako <xref:System.Windows.Forms.Panel>– nebo kontejneru třídy odvozené od <xref:System.Windows.Forms.Panel> (například <xref:System.Windows.Forms.FlowLayoutPanel> nebo <xref:System.Windows.Forms.TableLayoutPanel>) – ve formuláři. Pokud nastavíte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na kontejner, aby <xref:System.Windows.Forms.RightToLeft.Yes> a poté nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost na jeden nebo více ovládacích prvků uvnitř kontejner, aby <xref:System.Windows.Forms.AnchorStyles.Right>, pak žádný posuvník někdy se zobrazí. Třídy odvozené od <xref:System.Windows.Forms.ScrollableControl> funguje jako <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> byl nastaven <xref:System.Windows.Forms.RightToLeft.No>.  
  
 V současné době pouze řešením je vnořit <xref:System.Windows.Forms.ScrollableControl> uvnitř jiné <xref:System.Windows.Forms.ScrollableControl>. Například potřebujete-li <xref:System.Windows.Forms.TableLayoutPanel> pro práci v této situaci, můžete umístit ji uvnitř <xref:System.Windows.Forms.Panel> řízení a nastavte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel> k <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Zrcadlení  
 *Zrcadlení* odkazuje na Prohodit rozložení prvků uživatelského rozhraní tak, aby jejich tok zprava doleva. Ve formuláři Windows zrcadlené pro příklad, minimalizovat, maximalizovat a zavřít tlačítka zobrazí nejvíce vlevo v záhlaví okna, není nejvíce vpravo.  
  
 Nastavení formuláře nebo ovládacího prvku <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost `true` zpětná čtení pořadí prvků na formuláři, ale toto nastavení není reverse rozložení být zprava doleva – to znamená, nevytváří zrcadlení. Například nastavení vlastnosti nepřesouvá **minimalizaci**, **Maximalizovat**, a **Zavřít** tlačítka v záhlaví formuláře na levé straně formuláře. Podobně, některé ovládací prvky, jako například <xref:System.Windows.Forms.TreeView> řídit, vyžadují, aby bylo možné změnit jejich zobrazení na být vhodné pro arabštinu nebo hebrejštinu zrcadlení. Můžete zrcadlení tyto ovládací prvky podle nastavení <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastnost.  
  
 Můžete vytvořit zrcadlené verzích následující prvky:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Některé ovládací prvky jsou zapečetěné. Proto nelze odvodit nový ovládací prvek z nich. Patří mezi ně <xref:System.Windows.Forms.ImageList> a <xref:System.Windows.Forms.ProgressBar> ovládací prvky.  
  
## <a name="see-also"></a>Viz také:

[Obousměrná podpora pro webových aplikací ASP.NET](http://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[Globalizace aplikací Windows Forms](globalizing-windows-forms.md)
