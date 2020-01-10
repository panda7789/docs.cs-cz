---
title: Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: e80379700b43ed5d0e74ea890c2a0eafe67159e6
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740223"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="50a9e-102">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="50a9e-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="50a9e-103">Mnoho ovládacích prvků [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] má ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, ale některé ovládací prvky [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nemají v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]žádné ekvivalenty.</span><span class="sxs-lookup"><span data-stu-id="50a9e-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="50a9e-104">Toto téma porovnává typy ovládacích prvků poskytované těmito dvěma technologiemi.</span><span class="sxs-lookup"><span data-stu-id="50a9e-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="50a9e-105">Vzájemná spolupráce se dá vždycky používat k hostování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ch ovládacích prvků, které nemají ekvivalent ve vašich aplikacích založených na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="50a9e-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="50a9e-106">Následující tabulka ukazuje, které [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a komponenty mají ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí řízení.</span><span class="sxs-lookup"><span data-stu-id="50a9e-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="50a9e-107">ovládací prvek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50a9e-107">Windows Forms control</span></span>|<span data-ttu-id="50a9e-108">Ekvivalent ovládacího prvku WPF</span><span class="sxs-lookup"><span data-stu-id="50a9e-108">WPF equivalent control</span></span>|<span data-ttu-id="50a9e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50a9e-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="50a9e-110">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<span data-ttu-id="50a9e-111"><xref:System.Windows.Controls.ListBox> se složením.</span><span class="sxs-lookup"><span data-stu-id="50a9e-111"><xref:System.Windows.Controls.ListBox> with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="50a9e-112">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<span data-ttu-id="50a9e-113"><xref:System.Windows.Controls.ComboBox> nepodporuje automatické dokončování.</span><span class="sxs-lookup"><span data-stu-id="50a9e-113"><xref:System.Windows.Controls.ComboBox> does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<span data-ttu-id="50a9e-114"><xref:System.Windows.Controls.TextBox> a dva ovládací prvky <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="50a9e-114"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="50a9e-115">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<span data-ttu-id="50a9e-116"><xref:System.Windows.Controls.WrapPanel> Nebo <xref:System.Windows.Controls.StackPanel></span><span class="sxs-lookup"><span data-stu-id="50a9e-116"><xref:System.Windows.Controls.WrapPanel> or <xref:System.Windows.Controls.StackPanel></span></span>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="50a9e-117">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="50a9e-118">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<span data-ttu-id="50a9e-119"><xref:System.Windows.Window> nepodporuje podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="50a9e-119"><xref:System.Windows.Window> does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="50a9e-120">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-120">No equivalent control.</span></span>|<span data-ttu-id="50a9e-121">Žádná Nápověda F1.</span><span class="sxs-lookup"><span data-stu-id="50a9e-121">No F1 Help.</span></span> <span data-ttu-id="50a9e-122">Nápověda "Co je to tohle" nahrazuje popisy tlačítek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="50a9e-123">Posouvání je integrováno do kontejnerových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="50a9e-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="50a9e-124">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="50a9e-125">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-125">No equivalent control.</span></span>|<span data-ttu-id="50a9e-126">Můžete použít třídu <xref:System.Windows.Documents.Hyperlink> k hostování hypertextových odkazů v rámci obsahu toku.</span><span class="sxs-lookup"><span data-stu-id="50a9e-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="50a9e-127">Ovládací prvek <xref:System.Windows.Controls.ListView> poskytuje zobrazení podrobností jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="50a9e-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="50a9e-128">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<span data-ttu-id="50a9e-129">styly ovládacího prvku <xref:System.Windows.Controls.Menu> mohou navýšit chování a vzhled <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="50a9e-129"><xref:System.Windows.Controls.Menu> control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="50a9e-130">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<span data-ttu-id="50a9e-131"><xref:System.Windows.Controls.TextBox> a dva ovládací prvky <xref:System.Windows.Controls.Primitives.RepeatButton>.</span><span class="sxs-lookup"><span data-stu-id="50a9e-131"><xref:System.Windows.Controls.TextBox> and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="50a9e-132">Třída <xref:Microsoft.Win32.OpenFileDialog> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obálka kolem ovládacího prvku Win32.</span><span class="sxs-lookup"><span data-stu-id="50a9e-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="50a9e-133">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="50a9e-134">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="50a9e-135">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="50a9e-136">Žádný ekvivalentní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="50a9e-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="50a9e-137">Třída <xref:Microsoft.Win32.SaveFileDialog> je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obálka kolem ovládacího prvku Win32.</span><span class="sxs-lookup"><span data-stu-id="50a9e-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the Win32 control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<span data-ttu-id="50a9e-138"><xref:System.Windows.Controls.ToolBar> se složením.</span><span class="sxs-lookup"><span data-stu-id="50a9e-138"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="50a9e-139"><xref:System.Windows.Controls.ToolBar> se složením.</span><span class="sxs-lookup"><span data-stu-id="50a9e-139"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<span data-ttu-id="50a9e-140"><xref:System.Windows.Controls.ToolBar> se složením.</span><span class="sxs-lookup"><span data-stu-id="50a9e-140"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<span data-ttu-id="50a9e-141"><xref:System.Windows.Controls.ToolBar> se složením.</span><span class="sxs-lookup"><span data-stu-id="50a9e-141"><xref:System.Windows.Controls.ToolBar> with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="50a9e-142">Posouvání je integrováno do kontejnerových ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="50a9e-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<span data-ttu-id="50a9e-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="50a9e-143"><xref:System.Windows.Controls.Frame>, <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType></span></span>|<span data-ttu-id="50a9e-144">Ovládací prvek <xref:System.Windows.Controls.Frame> může hostovat stránky HTML.</span><span class="sxs-lookup"><span data-stu-id="50a9e-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="50a9e-145">Počínaje .NET Framework 3,5 SP1 může ovládací prvek <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> hostovat stránky HTML a také převrátit ovládací prvek <xref:System.Windows.Controls.Frame>.</span><span class="sxs-lookup"><span data-stu-id="50a9e-145">Starting in the .NET Framework 3.5 SP1, the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50a9e-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50a9e-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- <span data-ttu-id="50a9e-147">[Návrhář WPF pro vývojáře model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="50a9e-147">[WPF Designer for Windows Forms Developers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))</span></span>
- [<span data-ttu-id="50a9e-148">Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="50a9e-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="50a9e-149">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="50a9e-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="50a9e-150">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="50a9e-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
