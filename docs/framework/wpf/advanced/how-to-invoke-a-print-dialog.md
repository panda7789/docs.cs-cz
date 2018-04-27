---
title: 'Postupy: Vyvolání dialogového okna Tisk'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65ea65e13d3217466eeacdac4c386cc02c68b29a
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="a0420-102">Postupy: Vyvolání dialogového okna Tisk</span><span class="sxs-lookup"><span data-stu-id="a0420-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="a0420-103">Pokud chcete zadat možnost tisknout z aplikace, můžete jednoduše vytvořit a otevřete <xref:System.Windows.Controls.PrintDialog> objektu.</span><span class="sxs-lookup"><span data-stu-id="a0420-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0420-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0420-104">Example</span></span>  
 <span data-ttu-id="a0420-105"><xref:System.Windows.Controls.PrintDialog> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] úlohy odeslání.</span><span class="sxs-lookup"><span data-stu-id="a0420-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="a0420-106">Ovládací prvek se snadno používá a může být vytvořena pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód.</span><span class="sxs-lookup"><span data-stu-id="a0420-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="a0420-107">Následující příklad ukazuje, jak vytvořit instanci a otevřete ovládací prvek v kódu a jak tisknout z něj.</span><span class="sxs-lookup"><span data-stu-id="a0420-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="a0420-108">Také ukazuje, jak zajistit, aby dialogové okno bude uživatel možnost nastavení určitého rozsahu stránek.</span><span class="sxs-lookup"><span data-stu-id="a0420-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="a0420-109">Příklad kódu předpokládá, že je soubor FixedDocumentSequence.xps v kořenové složce jednotky C:.</span><span class="sxs-lookup"><span data-stu-id="a0420-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="a0420-110">Jakmile otevřete dialogové okno, budou uživatelé moci vybrat z tiskárny v počítači nainstalovanou.</span><span class="sxs-lookup"><span data-stu-id="a0420-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="a0420-111">Možnost výběru budou mít i [zapisovací modul dokumentů Microsoft XPS](http://go.microsoft.com/fwlink/?LinkId=147319) vytvořit [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] souboru místo.</span><span class="sxs-lookup"><span data-stu-id="a0420-111">They will also have the option of selecting the [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0420-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolu nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], které je popsané v tomto tématu byste neměli zaměňovat s <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součásti Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a0420-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="a0420-113">Přesněji řečeno, můžete použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metoda bez někdy otevření dialogu.</span><span class="sxs-lookup"><span data-stu-id="a0420-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="a0420-114">V smysl můžete využít jako komponentu neviditelný tisk ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a0420-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="a0420-115">Ale z důvodů výkonu by bylo vhodnější použít buď <xref:System.Printing.PrintQueue.AddJob%2A> metoda nebo jednoho z dalších <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="a0420-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="a0420-116">Další informace o tom najdete v tématu [programové soubory XPS tiskových](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) a.</span><span class="sxs-lookup"><span data-stu-id="a0420-116">For more about this, see [Programmatically Print XPS Files](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0420-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0420-117">See Also</span></span>  
 <xref:System.Windows.Controls.PrintDialog>  
 [<span data-ttu-id="a0420-118">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="a0420-118">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="a0420-119">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="a0420-119">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="a0420-120">Zapisovací modul dokumentů Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="a0420-120">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
