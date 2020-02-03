---
title: Obousměrná podpora
ms.date: 09/30/2017
helpviewer_keywords:
- globalization [Windows Forms], bi-directional support in Windows
- Windows Forms, international
- localization [Windows Forms], bi-directional support in Windows
- bi-directional language support [Windows Forms], Windows applications
- Windows Forms, bi-directional support
ms.openlocfilehash: 8b2e842fc08be78b74cede85927352fafca7bc8f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742076"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Obousměrná podpora pro formulářové aplikace Windows
Pomocí sady Visual Studio můžete vytvářet aplikace pro systém Windows, které podporují obousměrné (zprava doleva) jazyky, jako je arabština a hebrejština. To zahrnuje standardní formuláře, dialogová okna, formuláře MDI a všechny ovládací prvky, se kterými můžete pracovat v těchto formulářích – to znamená všechny objekty v oboru názvů <xref:System.Windows.Forms.Control>.

## <a name="culture-support"></a>Podpora jazykové verze
 Jazyková verze a nastavení jazykové verze uživatelského rozhraní určují, jak aplikace funguje s daty, časy, měnou a dalšími informacemi. Podpora pro jazykovou verzi a jazykovou verzi uživatelského rozhraní je pro obousměrné jazyky stejná jako pro všechny ostatní jazyky. Další informace naleznete v tématu [třídy specifické pro jazykovou verzi pro globální formuláře Windows a webové formuláře](/visualstudio/ide/globalizing-and-localizing-applications).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>Vlastnosti RightToLeft a RightToLeftLayout
 Základní třída <xref:System.Windows.Forms.Control>, ze které jsou odvozeny formuláře, obsahuje vlastnost <xref:System.Windows.Forms.Control.RightToLeft%2A>, kterou lze nastavit pro změnu pořadí čtení formuláře a jeho ovládacích prvků. Pokud nastavíte vlastnost <xref:System.Windows.Forms.Control.RightToLeft%2A> formuláře, ve výchozím nastavení zdědí ovládací prvky ve formuláři toto nastavení. Vlastnost <xref:System.Windows.Forms.Control.RightToLeft%2A> však lze nastavit také jednotlivě u většiny ovládacích prvků. Viz také [Postupy: zobrazení textu zprava doleva v model Windows Forms pro globalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 Účinek vlastnosti <xref:System.Windows.Forms.Control.RightToLeft%2A> se může lišit od jednoho ovládacího prvku k druhému. V některých ovládacích prvcích vlastnost nastavuje pouze pořadí čtení, jako v ovládacích prvcích <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ToolTip>. V jiných ovládacích prvcích vlastnost <xref:System.Windows.Forms.Control.RightToLeft%2A> mění pořadí čtení i rozložení. To zahrnuje ovládací prvky <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.CheckBox>. Jiné ovládací prvky vyžadují, aby byla vlastnost <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> použita pro zrcadlení rozložení zprava doleva. Následující tabulka poskytuje podrobnosti o tom, jak vlastnosti <xref:System.Windows.Forms.Control.RightToLeft%2A> a <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> ovlivňují jednotlivé ovládací prvky model Windows Forms.

|Ovládací prvek/součást|Účinek vlastnosti RightToLeft|Účinek vlastnosti RightToLeftLayout|Vyžaduje zrcadlení?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|Nastaví směr čtení zprava doleva. Obrátí <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>a <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Žádný vliv|Ne|
|<xref:System.Windows.Forms.CheckBox>|Zaškrtávací políčko se zobrazí na pravé straně textu.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.CheckedListBox>|Všechna zaškrtávací políčka se zobrazí na pravé straně textu.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ColorDialog>|Neovlivněno; závisí na jazyku operačního systému.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ComboBox>|Položky v ovládacím prvku pole se seznamem jsou zarovnané vpravo|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ContextMenu>|Zobrazí zarovnání vpravo se stejným pořadím čtení zprava doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.DataGrid>|Zobrazí zarovnání vpravo se stejným pořadím čtení zprava doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.DataGridView>|Ovlivňuje pořadí čtení zprava doleva a rozložení ovládacích prvků.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.DateTimePicker>|Neovlivněno; závisí na jazyku operačního systému.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.DomainUpDown>|Tlačítka nahoru a dolů zarovnané doleva|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ErrorProvider>|Nepodporuje se|Žádný vliv|Ne|
|<xref:System.Windows.Forms.FontDialog>|Závisí na jazyku operačního systému.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.Form>|Nastaví směr čtení zprava doleva a obrátí posuvníky.|Zrcadlí formulář|Ano|
|<xref:System.Windows.Forms.GroupBox>|Popisek se zobrazí zarovnané vpravo. Podřízené ovládací prvky mohou dědit tuto vlastnost.|Použití <xref:System.Windows.Forms.TableLayoutPanel> v rámci ovládacího prvku pro podporu zrcadlení zprava doleva|Ne|
|<xref:System.Windows.Forms.HScrollBar>|Začíná na posuvníku (palec) zarovnané vpravo.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ImageList>|Nepožadováno|Žádný vliv|Ne|
|<xref:System.Windows.Forms.Label>|Zobrazeno zarovnané doprava Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Žádný vliv|Ne|
|<xref:System.Windows.Forms.LinkLabel>|Zobrazeno zarovnané doprava Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ListBox>|Položky jsou zarovnány vpravo.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.ListView>|Nastaví pořadí čtení zprava doleva. prvky zůstávají zarovnané vlevo|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.MainMenu>|Zobrazeno v době běhu zarovnané doprava s pořadím čtení zprava doleva (ne v době návrhu)|Žádný vliv|Ne|
|<xref:System.Windows.Forms.MaskedTextBox>|Zobrazí text zprava doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.MonthCalendar>|Neovlivněno; závisí na jazyku operačního systému.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.NotifyIcon>|Nepodporuje se|Nepodporuje se|Ne|
|<xref:System.Windows.Forms.NumericUpDown>|Tlačítka nahoru a dolů jsou zarovnána doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.OpenFileDialog>|U operačních systémů, které jsou zprava doleva, nastavení vlastnosti <xref:System.Windows.Forms.Control.RightToLeft> obsahujícího formuláře na <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizaci dialogového okna |Žádný vliv|Ne|
|<xref:System.Windows.Forms.PageSetupDialog>|Neovlivněno; závisí na jazyku operačního systému.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.Panel>|Podřízené ovládací prvky mohou dědit tuto vlastnost.|Použití <xref:System.Windows.Forms.TableLayoutPanel> v rámci ovládacího prvku zprava doleva|Ano|
|<xref:System.Windows.Forms.PictureBox>|Nepodporuje se|Žádný vliv|Ne|
|<xref:System.Windows.Forms.PrintDialog>|Neovlivněno; závisí na jazyku operačního systému.|Žádný vliv|Ne|
|<xref:System.Drawing.Printing.PrintDocument>|Svislý posuvník zůstane zarovnaný doleva a vodorovný posuvník začne od levého sloupce.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.PrintPreviewDialog>|Nepodporuje se|Nepodporuje se|Ne|
|<xref:System.Windows.Forms.ProgressBar>|Nemá vliv na tuto vlastnost|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.RadioButton>|Přepínač se zobrazí na pravé straně textu.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.RichTextBox>|Prvky ovládacího prvku, které obsahují text, jsou zobrazeny zprava doleva s pořadím čtení ZPRAVa doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.SaveFileDialog>|Neovlivněno; závisí na jazyku operačního systému.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.SplitContainer>|Rozložení panelu je obrácené; na levé straně se zobrazí svislý posuvník. vodorovný posuvník začíná vpravo|Použití <xref:System.Windows.Forms.TableLayoutPanel> k zrcadlení pořadí podřízených ovládacích prvků|Ne|
|<xref:System.Windows.Forms.Splitter>|Nepodporuje se|Žádný vliv|Ne|
|<xref:System.Windows.Forms.StatusBar>|Nepodporováno; místo toho použít <xref:System.Windows.Forms.StatusStrip>|Bez účinku; místo toho použít <xref:System.Windows.Forms.StatusStrip>|Ne|
|<xref:System.Windows.Forms.TabControl>|Tato vlastnost nemá vliv.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.TextBox>|Zobrazí text zprava doleva s pořadím čtení ZPRAVa doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.Timer>|Nepožadováno|Nepožadováno|Ne|
|<xref:System.Windows.Forms.ToolBar>|Není ovlivněna touto vlastností; místo toho použít <xref:System.Windows.Forms.ToolStrip>|Bez účinku; místo toho použít <xref:System.Windows.Forms.ToolStrip>|Ano|
|<xref:System.Windows.Forms.ToolTip>|Nastaví směr čtení zprava doleva.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.TrackBar>|Posun nebo sledování začíná vpravo; Když je <xref:System.Windows.Forms.TrackBar.Orientation%2A> svislé, objeví se na pravé straně.|Žádný vliv|Ne|
|<xref:System.Windows.Forms.TreeView>|Nastaví pouze směr čtení zprava doleva.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.UserControl>|Na levé straně se zobrazí svislý posuvník. vodorovný posuvník má na pravé straně palec|Žádná přímá podpora; použít <xref:System.Windows.Forms.TableLayoutPanel>|Ne|
|<xref:System.Windows.Forms.VScrollBar>|Zobrazuje se na levé straně místo pravé strany ovládacích prvků s posuvníky.|Žádný vliv|Ne|

## <a name="encoding"></a>Kódování
 Model Windows Forms podporuje kódování Unicode, takže při vytváření obousměrných aplikací můžete zahrnout libovolnou znakovou sadu. Ne všechny ovládací prvky model Windows Forms ale podporují Unicode na všech platformách.

## <a name="gdi"></a>GDI+
 Pomocí rozhraní GDI+ můžete nakreslit text se stejným směrem, jako je čtení zprava doleva. Metoda <xref:System.Drawing.Graphics.DrawString%2A>, která se používá k vykreslování textu, podporuje parametr `StringFormat`, který lze nastavit na <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> člena <xref:System.Drawing.StringFormatFlags> výčtu, aby bylo možné vrátit počáteční bod pro text.

## <a name="common-dialog-boxes"></a>Společná dialogová okna
 Systémové nástroje, jako je dialogové okno otevřít soubor, jsou pod kontrolou systému Windows. Dědí jazykové prvky z operačního systému. Pokud používáte verzi systému Windows se správnými jazykovými nastaveními, budou Tato dialogová okna správně fungovat s obousměrnými jazyky.

 Podobně se okna zpráv přecházejí přes operační systém a podporují obousměrný text. Tlačítka titulků v okně se zprávou jsou založena na aktuálním nastavení jazyka. Ve výchozím nastavení se v oknech zpráv nepoužívají směr čtení zprava doleva, ale můžete zadat parametr pro změnu pořadí čtení při zobrazení oken se zprávami.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, ScrollBar a ovládací prvek ScrollableControl
 V současné době je model Windows Forms omezení, které brání všem třídám odvozeným od <xref:System.Windows.Forms.ScrollableControl> správně fungovat, pokud je povolená obě <xref:System.Windows.Forms.Control.RightToLeft%2A> a <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> je nastavená na <xref:System.Windows.Forms.RightToLeft.Yes>. Řekněme například, že umístíte ovládací prvek, jako je například <xref:System.Windows.Forms.Panel>, nebo třídu kontejneru odvozenou z <xref:System.Windows.Forms.Panel> (například <xref:System.Windows.Forms.FlowLayoutPanel> nebo <xref:System.Windows.Forms.TableLayoutPanel>) – na formuláři. Pokud nastavíte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> kontejneru na <xref:System.Windows.Forms.RightToLeft.Yes> a potom nastavíte vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> na jeden nebo více ovládacích prvků uvnitř kontejneru na <xref:System.Windows.Forms.AnchorStyles.Right>, pak se žádný posuvník nikdy nezobrazuje. Třída odvozená z <xref:System.Windows.Forms.ScrollableControl> funguje jako if <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> byla nastavena na <xref:System.Windows.Forms.RightToLeft.No>.

 V současné době je jediným alternativním řešením vnoření <xref:System.Windows.Forms.ScrollableControl> do jiného <xref:System.Windows.Forms.ScrollableControl>. Pokud třeba potřebujete <xref:System.Windows.Forms.TableLayoutPanel> v této situaci pracovat, můžete ji umístit do ovládacího prvku <xref:System.Windows.Forms.Panel> a nastavit <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel> na <xref:System.Windows.Forms.RightToLeft.Yes>.

## <a name="mirroring"></a>Zrcadlení
 *Zrcadlení* odkazuje na změnu rozložení prvků uživatelského rozhraní tak, aby byly v toku zprava doleva. V zrcadlovém formuláři systému Windows se tlačítka pro minimalizaci, maximalizaci a zavření zobrazují nejvíce vlevo na záhlaví, nikoli na pravé straně.

 Nastavení vlastnosti <xref:System.Windows.Forms.Control.RightToLeft%2A> formuláře nebo ovládacího prvku na hodnotu `true` obrátí pořadí čtení prvků ve formuláři, ale toto nastavení nevrátí rozložení na hodnotu zprava doleva – to znamená, že nezpůsobí zrcadlení. Například nastavením této vlastnosti nepřesunete tlačítka **minimalizovat**, **maximalizovat**a **Zavřít** v záhlaví formuláře na levou stranu formuláře. Podobně některé ovládací prvky, například ovládací prvek <xref:System.Windows.Forms.TreeView>, vyžadují zrcadlení, aby bylo možné změnit jejich zobrazení tak, aby bylo vhodné pro arabštinu nebo hebrejštinu. Tyto ovládací prvky lze zrcadlit nastavením vlastnosti <xref:System.Windows.Forms.Form.RightToLeftLayout%2A>.

 Můžete vytvořit zrcadlené verze následujících ovládacích prvků:

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Některé ovládací prvky jsou zapečetěné. Proto nemůžete z nich odvodit nový ovládací prvek. Mezi ně patří ovládací prvky <xref:System.Windows.Forms.ImageList> a <xref:System.Windows.Forms.ProgressBar>.

## <a name="see-also"></a>Viz také

- [Obousměrná podpora pro webové aplikace v ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
