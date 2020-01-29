---
title: Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: 7f531b60d8b31181688f3d0a6753b234ffc6c7dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735216"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a>Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF
Mnoho ovládacích prvků [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] má ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, ale některé ovládací prvky [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nemají v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]žádné ekvivalenty. Toto téma porovnává typy ovládacích prvků poskytované těmito dvěma technologiemi.  
  
 Vzájemná spolupráce se dá vždycky používat k hostování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ch ovládacích prvků, které nemají ekvivalent ve vašich aplikacích založených na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Následující tabulka ukazuje, které [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a komponenty mají ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí řízení.  
  
|ovládací prvek Windows Forms|Ekvivalent ovládacího prvku WPF|Poznámky|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> se složením.||  
|<xref:System.Windows.Forms.ColorDialog>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> nepodporuje automatické dokončování.|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> a dva ovládací prvky <xref:System.Windows.Controls.Primitives.RepeatButton>.||  
|<xref:System.Windows.Forms.ErrorProvider>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> Nebo <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.FontDialog>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> nepodporuje podřízená okna.|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|Žádný ekvivalentní ovládací prvek.|Žádná Nápověda F1. Nápověda "Co je to tohle" nahrazuje popisy tlačítek.|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|Posouvání je integrováno do kontejnerových ovládacích prvků.|  
|<xref:System.Windows.Forms.ImageList>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|Žádný ekvivalentní ovládací prvek.|Můžete použít třídu <xref:System.Windows.Documents.Hyperlink> k hostování hypertextových odkazů v rámci obsahu toku.|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|Ovládací prvek <xref:System.Windows.Controls.ListView> poskytuje zobrazení podrobností jen pro čtení.|  
|<xref:System.Windows.Forms.MaskedTextBox>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|styly ovládacího prvku <xref:System.Windows.Controls.Menu> mohou navýšit chování a vzhled <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> třídy.|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> a dva ovládací prvky <xref:System.Windows.Controls.Primitives.RepeatButton>.||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|Třída <xref:Microsoft.Win32.OpenFileDialog> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obálka kolem ovládacího prvku Win32.|  
|<xref:System.Windows.Forms.PageSetupDialog>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|Žádný ekvivalentní ovládací prvek.||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|Třída <xref:Microsoft.Win32.SaveFileDialog> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obálka kolem ovládacího prvku Win32.|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> se složením.||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> se složením.||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> se složením.||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> se složením.||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|Posouvání je integrováno do kontejnerových ovládacích prvků.|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|Ovládací prvek <xref:System.Windows.Controls.Frame> může hostovat stránky HTML.<br /><br /> Počínaje .NET Framework 3,5 SP1 může ovládací prvek <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> hostovat stránky HTML a také převrátit ovládací prvek <xref:System.Windows.Controls.Frame>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návrhář WPF pro vývojáře model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Migrace a interoperabilita](migration-and-interoperability.md)
