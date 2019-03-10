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
ms.openlocfilehash: f494d3176d72563a82b50fd5e077917e46045b91
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712277"
---
# <a name="bi-directional-support-for-windows-forms-applications"></a>Obousměrná podpora pro formulářové aplikace Windows
Visual Studio můžete vytvářet aplikace pro systém Windows, které podporují obousměrné (vpravo zprava doleva) jazyků, jako je arabština nebo hebrejština. To zahrnuje standardní formuláře, dialogová okna, formuláře MDI a ovládací prvky, které můžete pracovat s tyto formy – to znamená, že všechny objekty v <xref:System.Windows.Forms.Control> oboru názvů.  
  
## <a name="culture-support"></a>Podpora jazykové verze  
 Nastavení jazykové verze uživatelského rozhraní a jazykové verze určují, jak aplikace funguje se data, časy, měny a další informace. Podpora pro jazykové verze a jazykové verze uživatelského rozhraní je stejný pro obousměrných jazycích, jako je pro ostatní jazyky. Další informace najdete v tématu [specifické pro jazykovou verzi třídy pro globální formuláře Windows a webových formulářů](/visualstudio/ide/culture-specific-classes-for-global-windows-forms-and-web-forms).  
  
## <a name="righttoleft-and-righttoleftlayout-properties"></a>RightToLeft a vlastnosti RightToLeftLayout  
 Základní <xref:System.Windows.Forms.Control> zahrnuje třídy, ze které jsou odvozeny formulářů, <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost, která můžete nastavit, chcete-li změnit pořadí čtení formuláře a jejích ovládacích prvků. Pokud nastavíte formuláře <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost, výchozí ovládací prvky ve formuláři zdědí toto nastavení. Ale můžete také nastavit <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost jednotlivě na většině ovládací prvky. Viz také [jak: Zobrazení textu zprava doleva v modelu Windows Forms pro globalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100)).  
  
 Vliv <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost se může lišit od jeden ovládací prvek do jiného. V některé ovládací prvky vlastnost pouze nastaví pořadí čtení, stejně jako <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.TreeView> a <xref:System.Windows.Forms.ToolTip> ovládací prvky. V další ovládací prvky <xref:System.Windows.Forms.Control.RightToLeft%2A> změny vlastností pořadí čtení a rozložení. Jedná se o <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.CheckBox> ovládací prvky. Další ovládací prvky vyžadují, aby <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastnost jde použít pro zrcadlení její rozložení zprava doleva. Následující tabulka obsahuje podrobnosti o <xref:System.Windows.Forms.Control.RightToLeft%2A> a <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastnosti vliv jednotlivých ovládacích prvků Windows Forms.  
  
|Ovládací prvek nebo komponenty|Účinek vlastnost RightToLeft|Vlastnosti RightToLeftLayout platnost|Vyžaduje zrcadlení?|  
|------------------------|------------------------------------|------------------------------------------|-------------------------|  
|<xref:System.Windows.Forms.Button>|Nastaví RTL pořadí čtení. Obrátí <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>, <xref:System.Windows.Forms.ButtonBase.ImageAlign%2A>, a <xref:System.Windows.Forms.ButtonBase.TextImageRelation%2A>|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.CheckBox>|Zaškrtávací políčko se zobrazí na pravé straně textu|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.CheckedListBox>|Všechna zaškrtávací políčka jsou zobrazena na pravé straně textu|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ColorDialog>|Není ovlivněna; závisí na jazyku operačního systému|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ComboBox>|Položky v ovládacím prvku pole se seznamem jsou zarovnaná vpravo|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ContextMenu>|Zobrazí se zarovnaný doprava s směr čtení zprava doleva|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.DataGrid>|Zobrazí se zarovnaný doprava s směr čtení zprava doleva|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.DataGridView>|Má vliv na obou pořadí a řízení rozložení pro čtení zprava doleva.|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.DateTimePicker>|Není ovlivněna; závisí na jazyku operačního systému|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.DomainUpDown>|Vlevo – zarovná nahoru a dolů|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ErrorProvider>|Není podporováno|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.FontDialog>|Závisí na jazyku operačního systému|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.Form>|Nastaví pořadí čtení zprava doleva a obrátí posuvníky|Odráží formuláře|Ano|  
|<xref:System.Windows.Forms.GroupBox>|Popisek se zobrazí zarovnaný doprava. Tato vlastnost může dědit podřízených ovládacích prvků.|Použití <xref:System.Windows.Forms.TableLayoutPanel> podporu v rámci ovládacího prvku pro zrcadlení zprava doleva|Ne|  
|<xref:System.Windows.Forms.HScrollBar>|Začíná posuvníku (palce) zarovnaný doprava|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ImageList>|Nepožaduje se|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.Label>|Zobrazí zarovnaný doprava. Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.LinkLabel>|Zobrazí zarovnaný doprava. Obrátí <xref:System.Windows.Forms.Label.TextAlign%2A> a <xref:System.Windows.Forms.Label.ImageAlign%2A>|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ListBox>|Položky jsou zarovnaná vpravo|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.ListView>|Nastaví pořadí čtení zprava doleva; Zůstaňte prvky zarovnané vlevo|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.MainMenu>|U RTL pořadí čtení v době běhu (ne v době návrhu) zobrazí zarovnaný doprava|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.MaskedTextBox>|Zobrazí text zprava doleva.|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.MonthCalendar>|Není ovlivněna; závisí na jazyku operačního systému|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.NotifyIcon>|Není podporováno|Není podporováno|Ne|  
|<xref:System.Windows.Forms.NumericUpDown>|Nahoru a dolů jsou zarovnané vlevo|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.OpenFileDialog>|V operačních systémech zprava doleva, nastavení obsahující formulář <xref:System.Windows.Forms.Control.RightToLeft> vlastnost <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType> lokalizováno dialogového okna |Žádný vliv|Ne|  
|<xref:System.Windows.Forms.PageSetupDialog>|Není ovlivněna; závisí na jazyku operačního systému|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.Panel>|Podřízené ovládací prvky mohou dědit této vlastnosti|Použití <xref:System.Windows.Forms.TableLayoutPanel> v rámci ovládacího prvku pro právo levé podpory|Ano|  
|<xref:System.Windows.Forms.PictureBox>|Není podporováno|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.PrintDialog>|Není ovlivněna; závisí na jazyku operačního systému|Žádný vliv|Ne|  
|<xref:System.Drawing.Printing.PrintDocument>|Svislý posuvník budou zarovnané vlevo a vodorovného posuvníku začne z levé strany|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Není podporováno|Není podporováno|Ne|  
|<xref:System.Windows.Forms.ProgressBar>|Tato vlastnost vliv|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.RadioButton>|Přepínací tlačítko se zobrazí na pravé straně textu|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.RichTextBox>|Ovládací prvky, které obsahují text se zobrazí zleva doprava se směr čtení zprava doleva|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.SaveFileDialog>|Není ovlivněna; závisí na jazyku operačního systému|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.SplitContainer>|Panel rozložení je obrácený; na levé straně, se zobrazí svislý posuvník Vodorovný posuvník spustí z pravé strany|Použití <xref:System.Windows.Forms.TableLayoutPanel> zrcadlení pořadí podřízených ovládacích prvků|Ne|  
|<xref:System.Windows.Forms.Splitter>|Není podporováno|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.StatusBar>|Nejsou podporovány. použít <xref:System.Windows.Forms.StatusStrip> místo|Žádný vliv; použít <xref:System.Windows.Forms.StatusStrip> místo|Ne|  
|<xref:System.Windows.Forms.TabControl>|Není ovlivněna touto vlastností|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.TextBox>|Zobrazí text zprava doleva s směr čtení zprava doleva|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.Timer>|Nepožaduje se|Nepožaduje se|Ne|  
|<xref:System.Windows.Forms.ToolBar>|Není ovlivněna touto vlastností; použít <xref:System.Windows.Forms.ToolStrip> místo|Žádný vliv; použít <xref:System.Windows.Forms.ToolStrip> místo|Ano|  
|<xref:System.Windows.Forms.ToolTip>|Nastaví pořadí čtení zprava doleva.|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.TrackBar>|Posunout nebo sledovat spustí z pravé strany; Když <xref:System.Windows.Forms.TrackBar.Orientation%2A> je svislý, značky dojít z pravé strany|Žádný vliv|Ne|  
|<xref:System.Windows.Forms.TreeView>|Nastaví pouze směr čtení zprava doleva.|Odráží ovládacího prvku|Ano|  
|<xref:System.Windows.Forms.UserControl>|Na levé straně, se zobrazí svislý posuvník Vodorovný posuvník má jezdce na pravé straně|Nepodporuje přímé; použít <xref:System.Windows.Forms.TableLayoutPanel>|Ne|  
|<xref:System.Windows.Forms.VScrollBar>|Zobrazí na levé straně místo pravé straně posuvný ovládacích prvků|Žádný vliv|Ne|  
  
## <a name="encoding"></a>Kódování  
 Windows Forms podporu kódování Unicode, takže může obsahovat libovolný znak, nastavte při vytváření aplikace obousměrné. Ale ne všechny ovládací prvky Windows Forms podporuje kódování Unicode na všech platformách. Další informace najdete v tématu [kódování a globalizace Windows Forms](encoding-and-windows-forms-globalization.md).  
  
## <a name="gdi"></a>GDI+  
 Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] pro kreslení textu pomocí pořadí čtení zprava doleva. <xref:System.Drawing.Graphics.DrawString%2A> Podporuje metodu, která slouží k vykreslení textu, `StringFormat` parametr, který lze nastavit na <xref:System.Drawing.StringFormatFlags.DirectionRightToLeft> člena <xref:System.Drawing.StringFormatFlags> výčet, aby bylo možné reverse bod počátek pro text.  
  
## <a name="common-dialog-boxes"></a>Společná dialogová okna  
 V rámci ovládacího prvku Windows jsou systémové nástroje jako je například dialogovém okně Otevřít soubor. Elementy jazyka dědí z operačního systému. Pokud používáte verzi Windows pomocí nastavení správný jazyk, budou tyto dialogy s obousměrných jazycích fungovat správně.  
  
 Obdobně okna se zprávou projít operačního systému a podporují obousměrné text. Popisky tlačítek pole zprávy jsou založeny na aktuální nastavení jazyka. Ve výchozím nastavení okna se zprávou nepoužívejte pořadí čtení zprava doleva, ale zadáte parametr, chcete-li změnit pořadí čtení při zobrazení okna se zprávou.  
  
## <a name="righttoleft-scrollbars-and-scrollablecontrol"></a>RightToLeft posuvníky a ovládací prvek ScrollableControl  
 Aktuálně nejsou k dispozici omezení ve Windows Forms, který zabraňuje všechny třídy odvozené od <xref:System.Windows.Forms.ScrollableControl> z funguje správně při obě <xref:System.Windows.Forms.Control.RightToLeft%2A> je povolená a <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> je nastavena na <xref:System.Windows.Forms.RightToLeft.Yes>. Například Řekněme, jako například umístit ovládací prvek <xref:System.Windows.Forms.Panel>– nebo kontejner třída odvozená z <xref:System.Windows.Forms.Panel> (například <xref:System.Windows.Forms.FlowLayoutPanel> nebo <xref:System.Windows.Forms.TableLayoutPanel>) – na formuláři. Pokud nastavíte <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na kontejner, aby <xref:System.Windows.Forms.RightToLeft.Yes> a pak nastavte <xref:System.Windows.Forms.Control.Anchor%2A> vlastnosti na jednom nebo více ovládacích prvků uvnitř kontejneru <xref:System.Windows.Forms.AnchorStyles.Right>, pak žádný zobrazí posuvník, někdy. Třída odvozena z <xref:System.Windows.Forms.ScrollableControl> funguje jakoby <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> byly nastavené <xref:System.Windows.Forms.RightToLeft.No>.  
  
 V současné době jediným alternativním řešením je vnořit <xref:System.Windows.Forms.ScrollableControl> uvnitř jiného <xref:System.Windows.Forms.ScrollableControl>. Například pokud potřebujete <xref:System.Windows.Forms.TableLayoutPanel> pro práci v takové situaci je možné je umístit uvnitř <xref:System.Windows.Forms.Panel> ovládací prvek a nastavit <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> na <xref:System.Windows.Forms.Panel> k <xref:System.Windows.Forms.RightToLeft.Yes>.  
  
## <a name="mirroring"></a>Zrcadlení  
 *Zrcadlení* odkazuje na vrácení rozložení prvků uživatelského rozhraní tak, aby se tok zprava doleva. V zrcadlené formuláře Windows pro příklad, minimalizovat, maximalizovat a zavřít tlačítka zobrazí nejvíce vlevo v záhlaví okna, ne úplně vpravo.  
  
 Nastavení formuláře nebo ovládacího prvku <xref:System.Windows.Forms.Control.RightToLeft%2A> vlastnost `true` opakem pořadí čtení prvků na formuláři, ale toto nastavení zpětné rozložení zprava doleva – to znamená, že ho nezpůsobuje zrcadlení. Například nastavení této vlastnosti nepřesouvá **minimalizovat**, **Maximalizovat**, a **Zavřít** tlačítka v záhlaví okna formuláře na levou stranu formuláře. Podobně, některé ovládací prvky, jako <xref:System.Windows.Forms.TreeView> řídit, vyžadují, aby bylo možné změnit jejich zobrazení bude určena arabský nebo hebrejský zrcadlení. Tyto ovládací prvky podle nastavení můžete zrcadlit <xref:System.Windows.Forms.Form.RightToLeftLayout%2A> vlastnost.  
  
 Můžete vytvořit zrcadlených verze následující ovládací prvky:  
  
-   <xref:System.Windows.Forms.ColumnHeader.ListView%2A>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TabPage>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.TreeView>  
  
 Některé ovládací prvky jsou zapečetěné. Nový ovládací prvek proto nemůže odvozovat z nich. Patří mezi ně <xref:System.Windows.Forms.ImageList> a <xref:System.Windows.Forms.ProgressBar> ovládací prvky.  
  
## <a name="see-also"></a>Viz také:

- [Obousměrná podpora pro webové aplikace ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/6eedwbtt(v=vs.100))
- [Globalizace aplikací Windows Forms](globalizing-windows-forms.md)
