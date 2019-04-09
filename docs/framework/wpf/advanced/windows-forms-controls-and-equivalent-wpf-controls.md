---
title: Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
ms.assetid: 8a157e6b-8054-46db-a5cf-a78966acc7a1
ms.openlocfilehash: abfcb9f5398a6a8d264985543df585bea93a0446
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075272"
---
# <a name="windows-forms-controls-and-equivalent-wpf-controls"></a><span data-ttu-id="211e5-102">Ovládací prvky Windows Forms a ekvivalentní ovládací prvky WPF</span><span class="sxs-lookup"><span data-stu-id="211e5-102">Windows Forms Controls and Equivalent WPF Controls</span></span>
<span data-ttu-id="211e5-103">Mnoho [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků, ale některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nemají ekvivalent v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="211e5-103">Many [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] controls, but some [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls have no equivalents in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="211e5-104">Toto téma srovnává typy ovládacích prvků, které jsou k dispozici ve dvou technologií.</span><span class="sxs-lookup"><span data-stu-id="211e5-104">This topic compares control types provided by the two technologies.</span></span>  
  
 <span data-ttu-id="211e5-105">Vzájemná spolupráce grafického subsystému k hostiteli můžete kdykoli použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které nemají ekvivalent v vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.</span><span class="sxs-lookup"><span data-stu-id="211e5-105">You can always use interoperation to host [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls that do not have equivalents in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based applications.</span></span>  
  
 <span data-ttu-id="211e5-106">Následující tabulka uvádí, které [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a součásti mají ekvivalentní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládat funkce.</span><span class="sxs-lookup"><span data-stu-id="211e5-106">The following table shows which [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls and components have equivalent [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control functionality.</span></span>  
  
|<span data-ttu-id="211e5-107">ovládací prvek Windows Forms</span><span class="sxs-lookup"><span data-stu-id="211e5-107">Windows Forms control</span></span>|<span data-ttu-id="211e5-108">Ekvivalentní ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="211e5-108">WPF equivalent control</span></span>|<span data-ttu-id="211e5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="211e5-109">Remarks</span></span>|  
|---------------------------|----------------------------|-------------|  
|<xref:System.Windows.Forms.BindingNavigator>|<span data-ttu-id="211e5-110">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-110">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.BindingSource>|<xref:System.Windows.Data.CollectionViewSource>||  
|<xref:System.Windows.Forms.Button>|<xref:System.Windows.Controls.Button>||  
|<xref:System.Windows.Forms.CheckBox>|<xref:System.Windows.Controls.CheckBox>||  
|<xref:System.Windows.Forms.CheckedListBox>|<xref:System.Windows.Controls.ListBox> <span data-ttu-id="211e5-111">s složení.</span><span class="sxs-lookup"><span data-stu-id="211e5-111">with composition.</span></span>||  
|<xref:System.Windows.Forms.ColorDialog>|<span data-ttu-id="211e5-112">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-112">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ComboBox>|<xref:System.Windows.Controls.ComboBox>|<xref:System.Windows.Controls.ComboBox> <span data-ttu-id="211e5-113">nepodporuje automatické dokončování.</span><span class="sxs-lookup"><span data-stu-id="211e5-113">does not support auto-complete.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<xref:System.Windows.Controls.ContextMenu>||  
|<xref:System.Windows.Forms.DataGridView>|<xref:System.Windows.Controls.DataGrid>||  
|<xref:System.Windows.Forms.DateTimePicker>|<xref:System.Windows.Controls.DatePicker>||  
|<xref:System.Windows.Forms.DomainUpDown>|<xref:System.Windows.Controls.TextBox> <span data-ttu-id="211e5-114">a dvě <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="211e5-114">and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.ErrorProvider>|<span data-ttu-id="211e5-115">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-115">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FlowLayoutPanel>|<xref:System.Windows.Controls.WrapPanel> <span data-ttu-id="211e5-116">or</span><span class="sxs-lookup"><span data-stu-id="211e5-116">or</span></span> <xref:System.Windows.Controls.StackPanel>||  
|<xref:System.Windows.Forms.FolderBrowserDialog>|<span data-ttu-id="211e5-117">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-117">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.FontDialog>|<span data-ttu-id="211e5-118">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-118">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Window>|<xref:System.Windows.Window> <span data-ttu-id="211e5-119">nepodporuje podřízená okna.</span><span class="sxs-lookup"><span data-stu-id="211e5-119">does not support child windows.</span></span>|  
|<xref:System.Windows.Forms.GroupBox>|<xref:System.Windows.Controls.GroupBox>||  
|<xref:System.Windows.Forms.HelpProvider>|<span data-ttu-id="211e5-120">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-120">No equivalent control.</span></span>|<span data-ttu-id="211e5-121">Není žádná Nápověda F1.</span><span class="sxs-lookup"><span data-stu-id="211e5-121">No F1 Help.</span></span> <span data-ttu-id="211e5-122">"Co je to" nápovědy se nahrazuje popisy tlačítek.</span><span class="sxs-lookup"><span data-stu-id="211e5-122">"What's This" Help is replaced by ToolTips.</span></span>|  
|<xref:System.Windows.Forms.HScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="211e5-123">Posouvání je integrovaná do kontejnerů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="211e5-123">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.ImageList>|<span data-ttu-id="211e5-124">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-124">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Label>|<xref:System.Windows.Controls.Label>||  
|<xref:System.Windows.Forms.LinkLabel>|<span data-ttu-id="211e5-125">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-125">No equivalent control.</span></span>|<span data-ttu-id="211e5-126">Můžete použít <xref:System.Windows.Documents.Hyperlink> třídy pro hostitele hypertextové odkazy do plovoucího obsahu.</span><span class="sxs-lookup"><span data-stu-id="211e5-126">You can use the <xref:System.Windows.Documents.Hyperlink> class to host hyperlinks within flow content.</span></span>|  
|<xref:System.Windows.Forms.ListBox>|<xref:System.Windows.Controls.ListBox>||  
|<xref:System.Windows.Forms.ListView>|<xref:System.Windows.Controls.ListView>|<span data-ttu-id="211e5-127"><xref:System.Windows.Controls.ListView> Řízení poskytuje zobrazení jen pro čtení podrobností.</span><span class="sxs-lookup"><span data-stu-id="211e5-127">The <xref:System.Windows.Controls.ListView> control provides a read-only details view.</span></span>|  
|<xref:System.Windows.Forms.MaskedTextBox>|<span data-ttu-id="211e5-128">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-128">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.MenuStrip>|<xref:System.Windows.Controls.Menu>|<xref:System.Windows.Controls.Menu> <span data-ttu-id="211e5-129">používání stylů pro ovládací prvek můžete ji odhadnout chování a vzhled <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="211e5-129">control styling can approximate the behavior and appearance of the <xref:System.Windows.Forms.ToolStripProfessionalRenderer?displayProperty=nameWithType> class.</span></span>|  
|<xref:System.Windows.Forms.MonthCalendar>|<xref:System.Windows.Controls.Calendar>||  
|<xref:System.Windows.Forms.NotifyIcon>|<span data-ttu-id="211e5-130">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-130">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.NumericUpDown>|<xref:System.Windows.Controls.TextBox> <span data-ttu-id="211e5-131">a dvě <xref:System.Windows.Controls.Primitives.RepeatButton> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="211e5-131">and two <xref:System.Windows.Controls.Primitives.RepeatButton> controls.</span></span>||  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:Microsoft.Win32.OpenFileDialog>|<span data-ttu-id="211e5-132"><xref:Microsoft.Win32.OpenFileDialog> Třída je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obálku kolem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="211e5-132">The <xref:Microsoft.Win32.OpenFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.PageSetupDialog>|<span data-ttu-id="211e5-133">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-133">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.Panel>|<xref:System.Windows.Controls.Canvas>||  
|<xref:System.Windows.Forms.PictureBox>|<xref:System.Windows.Controls.Image>||  
|<xref:System.Windows.Forms.PrintDialog>|<xref:System.Windows.Controls.PrintDialog>||  
|<xref:System.Drawing.Printing.PrintDocument>|<span data-ttu-id="211e5-134">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-134">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.PrintPreviewControl>|<xref:System.Windows.Controls.DocumentViewer>||  
|<xref:System.Windows.Forms.PrintPreviewDialog>|<span data-ttu-id="211e5-135">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-135">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.ProgressBar>|<xref:System.Windows.Controls.ProgressBar>||  
|<xref:System.Windows.Forms.PropertyGrid>|<span data-ttu-id="211e5-136">Žádný odpovídající ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="211e5-136">No equivalent control.</span></span>||  
|<xref:System.Windows.Forms.RadioButton>|<xref:System.Windows.Controls.RadioButton>||  
|<xref:System.Windows.Forms.RichTextBox>|<xref:System.Windows.Controls.RichTextBox>||  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:Microsoft.Win32.SaveFileDialog>|<span data-ttu-id="211e5-137"><xref:Microsoft.Win32.SaveFileDialog> Třída je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obálku kolem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="211e5-137">The <xref:Microsoft.Win32.SaveFileDialog> class is a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wrapper around the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] control.</span></span>|  
|<xref:System.Windows.Forms.ScrollableControl>|<xref:System.Windows.Controls.ScrollViewer>||  
|<xref:System.Media.SoundPlayer>|<xref:System.Windows.Media.MediaPlayer>||  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Controls.GridSplitter>||  
|<xref:System.Windows.Forms.StatusStrip>|<xref:System.Windows.Controls.Primitives.StatusBar>||  
|<xref:System.Windows.Forms.TabControl>|<xref:System.Windows.Controls.TabControl>||  
|<xref:System.Windows.Forms.TableLayoutPanel>|<xref:System.Windows.Controls.Grid>||  
|<xref:System.Windows.Forms.TextBox>|<xref:System.Windows.Controls.TextBox>||  
|<xref:System.Windows.Forms.Timer>|<xref:System.Windows.Threading.DispatcherTimer>||  
|<xref:System.Windows.Forms.ToolStrip>|<xref:System.Windows.Controls.ToolBar>||  
|<xref:System.Windows.Forms.ToolStripContainer>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="211e5-138">s složení.</span><span class="sxs-lookup"><span data-stu-id="211e5-138">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="211e5-139">s složení.</span><span class="sxs-lookup"><span data-stu-id="211e5-139">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripDropDownMenu>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="211e5-140">s složení.</span><span class="sxs-lookup"><span data-stu-id="211e5-140">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolStripPanel>|<xref:System.Windows.Controls.ToolBar> <span data-ttu-id="211e5-141">s složení.</span><span class="sxs-lookup"><span data-stu-id="211e5-141">with composition.</span></span>||  
|<xref:System.Windows.Forms.ToolTip>|<xref:System.Windows.Controls.ToolTip>||  
|<xref:System.Windows.Forms.TrackBar>|<xref:System.Windows.Controls.Slider>||  
|<xref:System.Windows.Forms.TreeView>|<xref:System.Windows.Controls.TreeView>||  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Controls.UserControl>||  
|<xref:System.Windows.Forms.VScrollBar>|<xref:System.Windows.Controls.Primitives.ScrollBar>|<span data-ttu-id="211e5-142">Posouvání je integrovaná do kontejnerů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="211e5-142">Scrolling is built into container controls.</span></span>|  
|<xref:System.Windows.Forms.WebBrowser>|<xref:System.Windows.Controls.Frame><span data-ttu-id="211e5-143">, </span><span class="sxs-lookup"><span data-stu-id="211e5-143">,</span></span> <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType>|<span data-ttu-id="211e5-144"><xref:System.Windows.Controls.Frame> Ovládací prvek může být hostitelem stránek HTML.</span><span class="sxs-lookup"><span data-stu-id="211e5-144">The <xref:System.Windows.Controls.Frame> control can host HTML pages.</span></span><br /><br /> <span data-ttu-id="211e5-145">Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> ovládací prvek může být hostitelem stránky HTML a také zpětných <xref:System.Windows.Controls.Frame> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="211e5-145">Starting in the [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], the <xref:System.Windows.Controls.WebBrowser?displayProperty=nameWithType> control can host HTML pages and also backs the <xref:System.Windows.Controls.Frame> control.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="211e5-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="211e5-146">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="211e5-147">WPF Designer pro Windows Forms vývojáře</span><span class="sxs-lookup"><span data-stu-id="211e5-147">WPF Designer for Windows Forms Developers</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cc165605(v=vs.100))
- [<span data-ttu-id="211e5-148">Návod: Hostování ovládacího prvku Windows Forms ve WPF</span><span class="sxs-lookup"><span data-stu-id="211e5-148">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="211e5-149">Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="211e5-149">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="211e5-150">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="211e5-150">Migration and Interoperability</span></span>](migration-and-interoperability.md)
