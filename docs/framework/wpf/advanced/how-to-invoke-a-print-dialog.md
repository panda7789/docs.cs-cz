---
title: 'Postupy: Vyvolání dialogového okna Tisk'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 6d7bc322079718d17a921ef34af79145b021e3a7
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636091"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="1deb4-102">Postupy: Vyvolání dialogového okna Tisk</span><span class="sxs-lookup"><span data-stu-id="1deb4-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="1deb4-103">Chcete-li umožnit tisk z vaší aplikace, můžete jednoduše vytvořit a otevřít objekt <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="1deb4-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1deb4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1deb4-104">Example</span></span>  
 <span data-ttu-id="1deb4-105">Ovládací prvek <xref:System.Windows.Controls.PrintDialog> poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a odeslání úlohy ve formátu XPS.</span><span class="sxs-lookup"><span data-stu-id="1deb4-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="1deb4-106">Ovládací prvek lze snadno použít a vytvořit jeho instanci pomocí kódu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="1deb4-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="1deb4-107">Následující příklad ukazuje, jak vytvořit instanci a otevřít ovládací prvek v kódu a jak z něho tisknout.</span><span class="sxs-lookup"><span data-stu-id="1deb4-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="1deb4-108">Také ukazuje, jak zajistit, aby měl dialog uživateli možnost nastavení konkrétního rozsahu stránek.</span><span class="sxs-lookup"><span data-stu-id="1deb4-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="1deb4-109">Vzorový kód předpokládá, že v kořenu jednotky C: je soubor FixedDocumentSequence. XPS.</span><span class="sxs-lookup"><span data-stu-id="1deb4-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="1deb4-110">Po otevření dialogového okna budou uživatelé moci vybírat z tiskáren nainstalovaných v počítači.</span><span class="sxs-lookup"><span data-stu-id="1deb4-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="1deb4-111">Budou mít taky možnost vybrat [zapisovač dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319) a místo tisku vytvořit soubor XPS (XML Paper Specification).</span><span class="sxs-lookup"><span data-stu-id="1deb4-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1deb4-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> ovládací prvek WPF, který je popsán v tomto tématu, by neměl být zaměněn pomocí <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> součásti model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1deb4-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="1deb4-113">Výhradně řečeno, můžete použít metodu <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> bez předchozího otevření dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="1deb4-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="1deb4-114">V takovém smyslu lze ovládací prvek použít jako nepřehlednou tiskovou komponentu.</span><span class="sxs-lookup"><span data-stu-id="1deb4-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="1deb4-115">Ale z důvodů výkonu by bylo lepší použít buď metodu <xref:System.Printing.PrintQueue.AddJob%2A>, nebo jednu z mnoha <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="1deb4-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="1deb4-116">Další informace najdete v tématu [programové tiskové soubory XPS](how-to-programmatically-print-xps-files.md) a.</span><span class="sxs-lookup"><span data-stu-id="1deb4-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1deb4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1deb4-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="1deb4-118">Dokumenty v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="1deb4-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="1deb4-119">Přehled tisku</span><span class="sxs-lookup"><span data-stu-id="1deb4-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="1deb4-120">Zapisovač dokumentů Microsoft XPS</span><span class="sxs-lookup"><span data-stu-id="1deb4-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
