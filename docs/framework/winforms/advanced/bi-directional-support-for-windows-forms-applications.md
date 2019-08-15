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
ms.openlocfilehash: 5615ec6125cf622d4d6cd72d219d13be4bd5b096
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040402"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Obousměrná podpora pro formulářové aplikace Windows
Pomocí sady Visual Studio můžete vytvářet aplikace pro systém Windows, které podporují obousměrné (zprava doleva) jazyky, jako je arabština a hebrejština. To zahrnuje standardní formuláře, dialogová okna, formuláře MDI a všechny ovládací prvky, se kterými můžete pracovat v těchto formulářích – to znamená všechny objekty v <xref:System.Windows.Forms.Control> oboru názvů.

## <a name="culture-support"></a>Podpora jazykové verze
 Jazyková verze a nastavení jazykové verze uživatelského rozhraní určují, jak aplikace funguje s daty, časy, měnou a dalšími informacemi. Podpora pro jazykovou verzi a jazykovou verzi uživatelského rozhraní je pro obousměrné jazyky stejná jako pro všechny ostatní jazyky. Další informace naleznete v tématu [třídy specifické pro jazykovou verzi pro globální formuláře Windows a webové formuláře](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).

## <a name="righttoleft-and-righttoleftlayout-properties"></a>Vlastnosti RightToLeft a RightToLeftLayout
 Základní <xref:System.Windows.Forms.Control> třída, ze které jsou odvozeny formuláře, <xref:System.Windows.Forms.Control.RightToLeft%2A> obsahuje vlastnost, kterou lze nastavit pro změnu pořadí čtení formuláře a jeho ovládacích prvků. Pokud nastavíte <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost formuláře, zdědí toto nastavení ve výchozím nastavení ovládací prvky ve formuláři. <xref:System.Windows.Forms.Control.RightToLeft%2A> Vlastnost však můžete nastavit také jednotlivě u většiny ovládacích prvků. Podívejte [se také na postupy: Umožňuje zobrazit v model Windows Forms text zprava doleva pro globalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).

 Účinek <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnosti se může lišit od jednoho ovládacího prvku k druhému. V některých ovládacích prvcích vlastnost nastavuje pouze pořadí čtení, jako v <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.TreeView> ovládacích prvcích a <xref:System.Windows.Forms.ToolTip> . V jiných ovládacích prvcích <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost mění pořadí čtení i rozložení. To zahrnuje <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.ComboBox> ovládací prvky a. <xref:System.Windows.Forms.CheckBox> Jiné ovládací prvky vyžadují, <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> aby byla vlastnost použita pro zrcadlení rozložení zprava doleva. Následující tabulka poskytuje podrobnosti o tom, jak <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnosti <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> a ovlivňují jednotlivé ovládací prvky model Windows Forms.

|Ovládací prvek/součást|Účinek vlastnosti RightToLeft|Účinek vlastnosti RightToLeftLayout|Vyžaduje zrcadlení?|
|------------------------|------------------------------------|------------------------------------------|-------------------------|
|<xref:System.Windows.Forms.Button>|Nastaví směr čtení zprava doleva. Vrátí zpět <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>,a. <xref:System.Windows.Forms.ButtonBase.TextAlign%2A><xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Bez efektu|Ne|
|<xref:System.Windows.Forms.CheckBox>|Zaškrtávací políčko se zobrazí na pravé straně textu.|Bez efektu|Ne|
|<xref:System.Windows.Forms.CheckedListBox>|Všechna zaškrtávací políčka se zobrazí na pravé straně textu.|Bez efektu|Ne|
|<xref:System.Windows.Forms.ColorDialog>|Neovlivněno; závisí na jazyku operačního systému.|Bez efektu|Ne|
|<xref:System.Windows.Forms.ComboBox>|Položky v ovládacím prvku pole se seznamem jsou zarovnané vpravo|Bez efektu|Ne|
|<xref:System.Windows.Forms.ContextMenu>|Zobrazí zarovnání vpravo se stejným pořadím čtení zprava doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.DataGrid>|Zobrazí zarovnání vpravo se stejným pořadím čtení zprava doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.DataGridView>|Ovlivňuje pořadí čtení zprava doleva a rozložení ovládacích prvků.|Bez efektu|Ne|
|<xref:System.Windows.Forms.DateTimePicker>|Neovlivněno; závisí na jazyku operačního systému.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.DomainUpDown>|Tlačítka nahoru a dolů zarovnané doleva|Bez efektu|Ne|
|<xref:System.Windows.Forms.ErrorProvider>|Není podporováno|Bez efektu|Ne|
|<xref:System.Windows.Forms.FontDialog>|Závisí na jazyku operačního systému.|Bez efektu|Ne|
|<xref:System.Windows.Forms.Form>|Nastaví směr čtení zprava doleva a obrátí posuvníky.|Zrcadlí formulář|Ano|
|<xref:System.Windows.Forms.GroupBox>|Popisek se zobrazí zarovnané vpravo. Podřízené ovládací prvky mohou dědit tuto vlastnost.|<xref:System.Windows.Forms.TableLayoutPanel> Použití v rámci ovládacího prvku pro podporu zrcadlení zprava doleva|Ne|
|<xref:System.Windows.Forms.HScrollBar>|Začíná na posuvníku (palec) zarovnané vpravo.|Bez efektu|Ne|
|<xref:System.Windows.Forms.ImageList>|Nepožadováno|Bez efektu|Ne|
|<xref:System.Windows.Forms.Label>|Zobrazeno zarovnané doprava <xref:System.Windows.Forms.Label.TextAlign%2A> Obrátí a<xref:System.Windows.Forms.Label.ImageAlign%2A>|Bez efektu|Ne|
|<xref:System.Windows.Forms.LinkLabel>|Zobrazeno zarovnané doprava <xref:System.Windows.Forms.Label.TextAlign%2A> Obrátí a<xref:System.Windows.Forms.Label.ImageAlign%2A>|Bez efektu|Ne|
|<xref:System.Windows.Forms.ListBox>|Položky jsou zarovnány vpravo.|Bez efektu|Ne|
|<xref:System.Windows.Forms.ListView>|Nastaví pořadí čtení zprava doleva. prvky zůstávají zarovnané vlevo|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.MainMenu>|Zobrazeno v době běhu zarovnané doprava s pořadím čtení zprava doleva (ne v době návrhu)|Bez efektu|Ne|
|<xref:System.Windows.Forms.MaskedTextBox>|Zobrazí text zprava doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.MonthCalendar>|Neovlivněno; závisí na jazyku operačního systému.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.NotifyIcon>|Není podporováno|Není podporováno|Ne|
|<xref:System.Windows.Forms.NumericUpDown>|Tlačítka nahoru a dolů jsou zarovnána doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.OpenFileDialog>|V případě operačních systémů, které jsou zprava doleva, nastavení <xref:System.Windows.Forms.Control.RightToLeft> vlastnosti obsahujícího formuláře na <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizaci dialogového okna |Bez efektu|Ne|
|<xref:System.Windows.Forms.PageSetupDialog>|Neovlivněno; závisí na jazyku operačního systému.|Bez efektu|Ne|
|<xref:System.Windows.Forms.Panel>|Podřízené ovládací prvky mohou dědit tuto vlastnost.|Použití <xref:System.Windows.Forms.TableLayoutPanel> v rámci ovládacího prvku pro pravou a levou pomoc|Ano|
|<xref:System.Windows.Forms.PictureBox>|Není podporováno|Bez efektu|Ne|
|<xref:System.Windows.Forms.PrintDialog>|Neovlivněno; závisí na jazyku operačního systému.|Bez efektu|Ne|
|<xref:System.Drawing.Printing.PrintDocument>|Svislý posuvník zůstane zarovnaný doleva a vodorovný posuvník začne od levého sloupce.|Bez efektu|Ne|
|<xref:System.Windows.Forms.PrintPreviewDialog>|Není podporováno|Není podporováno|Ne|
|<xref:System.Windows.Forms.ProgressBar>|Nemá vliv na tuto vlastnost|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.RadioButton>|Přepínač se zobrazí na pravé straně textu.|Bez efektu|Ne|
|<xref:System.Windows.Forms.RichTextBox>|Prvky ovládacího prvku, které obsahují text, jsou zobrazeny zprava doleva s pořadím čtení ZPRAVa doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.SaveFileDialog>|Neovlivněno; závisí na jazyku operačního systému.|Bez efektu|Ne|
|<xref:System.Windows.Forms.SplitContainer>|Rozložení panelu je obrácené; na levé straně se zobrazí svislý posuvník. vodorovný posuvník začíná vpravo|<xref:System.Windows.Forms.TableLayoutPanel> Použití pro zrcadlení pořadí podřízených ovládacích prvků|Ne|
|<xref:System.Windows.Forms.Splitter>|Není podporováno|Bez efektu|Ne|
|<xref:System.Windows.Forms.StatusBar>|Nepodporováno; použít <xref:System.Windows.Forms.StatusStrip> místo toho|Bez účinku; použít <xref:System.Windows.Forms.StatusStrip> místo toho|Ne|
|<xref:System.Windows.Forms.TabControl>|Tato vlastnost nemá vliv.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.TextBox>|Zobrazí text zprava doleva s pořadím čtení ZPRAVa doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.Timer>|Nepožadováno|Nepožadováno|Ne|
|<xref:System.Windows.Forms.ToolBar>|Není ovlivněna touto vlastností; použít <xref:System.Windows.Forms.ToolStrip> místo toho|Bez účinku; použít <xref:System.Windows.Forms.ToolStrip> místo toho|Ano|
|<xref:System.Windows.Forms.ToolTip>|Nastaví směr čtení zprava doleva.|Bez efektu|Ne|
|<xref:System.Windows.Forms.TrackBar>|Posun nebo sledování začíná vpravo; Když <xref:System.Windows.Forms.TrackBar.Orientation%2A> je vertikální, objeví se na pravé straně.|Bez efektu|Ne|
|<xref:System.Windows.Forms.TreeView>|Nastaví pouze směr čtení zprava doleva.|Zrcadlit ovládací prvek|Ano|
|<xref:System.Windows.Forms.UserControl>|Na levé straně se zobrazí svislý posuvník. vodorovný posuvník má na pravé straně palec|Žádná přímá podpora; použít<xref:System.Windows.Forms.TableLayoutPanel>|Ne|
|<xref:System.Windows.Forms.VScrollBar>|Zobrazuje se na levé straně místo pravé strany ovládacích prvků s posuvníky.|Bez efektu|Ne|

## <a name="encoding"></a>Kódování
 Model Windows Forms podporuje kódování Unicode, takže při vytváření obousměrných aplikací můžete zahrnout libovolnou znakovou sadu. Ne všechny ovládací prvky model Windows Forms ale podporují Unicode na všech platformách. Další informace naleznete v tématu [Encoding and model Windows Forms Globalization](encoding-and-windows-forms-globalization.md).

## <a name="gdi"></a>GDI+
 Pomocí rozhraní GDI+ můžete nakreslit text se stejným směrem, jako je čtení zprava doleva. Metoda, která se používá k vykreslování textu, `StringFormat` podporuje parametr, který lze nastavit <xref:System.Drawing.StringFormatFlags> na <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> člen výčtu, aby bylo možné vrátit počáteční bod textu. <xref:System.Drawing.Graphics.DrawString%2A>

## <a name="common-dialog-boxes"></a>Společná dialogová okna
 Systémové nástroje, jako je dialogové okno otevřít soubor, jsou pod kontrolou systému Windows. Dědí jazykové prvky z operačního systému. Pokud používáte verzi systému Windows se správnými jazykovými nastaveními, budou Tato dialogová okna správně fungovat s obousměrnými jazyky.

 Podobně se okna zpráv přecházejí přes operační systém a podporují obousměrný text. Tlačítka titulků v okně se zprávou jsou založena na aktuálním nastavení jazyka. Ve výchozím nastavení se v oknech zpráv nepoužívají směr čtení zprava doleva, ale můžete zadat parametr pro změnu pořadí čtení při zobrazení oken se zprávami.

## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft, ScrollBar a ovládací prvek ScrollableControl
 V současné době je omezení model Windows Forms, <xref:System.Windows.Forms.ScrollableControl> které brání všem třídám odvozeným z aplikace správně, <xref:System.Windows.Forms.Control.RightToLeft%2A> Pokud je povolena a <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> nastavena na <xref:System.Windows.Forms.RightToLeft.Yes>. Řekněme například, že umístíte ovládací prvek, <xref:System.Windows.Forms.Panel>jako je, nebo třídu kontejneru odvozený od <xref:System.Windows.Forms.Panel> (například <xref:System.Windows.Forms.FlowLayoutPanel> nebo <xref:System.Windows.Forms.TableLayoutPanel>) – na formuláři. Pokud jste v <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> <xref:System.Windows.Forms.RightToLeft.Yes> kontejneru nastavili a pak nastavili <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost na jeden nebo více ovládacích prvků uvnitř kontejneru na <xref:System.Windows.Forms.AnchorStyles.Right>, pak se žádný posuvník nikdy nezobrazí. Třída odvozená od <xref:System.Windows.Forms.ScrollableControl> funguje jako if <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> byla nastavena na <xref:System.Windows.Forms.RightToLeft.No>.

 V současné době je jediným alternativním řešením vnoření <xref:System.Windows.Forms.ScrollableControl> uvnitř druhého <xref:System.Windows.Forms.ScrollableControl>. <xref:System.Windows.Forms.TableLayoutPanel> Například pokud potřebujete v této situaci pracovat, můžete ji umístit dovnitř <xref:System.Windows.Forms.Panel> <xref:System.Windows.Forms.Panel> ovládacího prvku <xref:System.Windows.Forms.RightToLeft.Yes>a nastavit <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na.

## <a name="mirroring"></a>Zrcadlení
 *Zrcadlení* odkazuje na změnu rozložení prvků uživatelského rozhraní tak, aby byly v toku zprava doleva. V zrcadlovém formuláři systému Windows se tlačítka pro minimalizaci, maximalizaci a zavření zobrazují nejvíce vlevo na záhlaví, nikoli na pravé straně.

 Nastavení <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnosti formuláře nebo ovládacího prvku pro `true` obrácené pořadí čtení prvků ve formuláři, ale toto nastavení nevrátí rozložení na hodnotu zprava doleva – to znamená, že nezpůsobí zrcadlení. Například nastavením této vlastnosti nepřesunete tlačítka **minimalizovat**, **maximalizovat**a **Zavřít** v záhlaví formuláře na levou stranu formuláře. Podobně některé ovládací prvky, například <xref:System.Windows.Forms.TreeView> ovládací prvek, vyžadují zrcadlení, aby bylo možné změnit jejich zobrazení tak, aby bylo vhodné pro arabštinu nebo hebrejštinu. Tyto ovládací prvky <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> lze zrcadlit nastavením vlastnosti.

 Můžete vytvořit zrcadlené verze následujících ovládacích prvků:

- <xref:System.Windows.Forms.ColumnHeader.ListView%2A>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TabPage>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.TreeView>

 Některé ovládací prvky jsou zapečetěné. Proto nemůžete z nich odvodit nový ovládací prvek. Mezi ně patří <xref:System.Windows.Forms.ImageList> ovládací <xref:System.Windows.Forms.ProgressBar> prvky a.

## <a name="see-also"></a>Viz také:

- [Obousměrná podpora pro webové aplikace v ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
- [Globalizace model Windows Formsch aplikací](globalizing-windows-forms.md)
