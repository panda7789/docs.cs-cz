---
title: Přehled ovládacího prvku PrintPreviewControl
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741437"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="53cc6-102">PrintPreviewControl – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="53cc6-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="53cc6-103"><xref:System.Windows.Forms.PrintPreviewControl> model Windows Forms se používá k zobrazení [PrintDocument](printdocument-component-windows-forms.md) , jak se zobrazí po vytištění.</span><span class="sxs-lookup"><span data-stu-id="53cc6-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="53cc6-104">Tento ovládací prvek nemá žádná tlačítka ani jiné prvky uživatelského rozhraní, takže se <xref:System.Windows.Forms.PrintPreviewControl> obvykle používá pouze v případě, že chcete napsat vlastní uživatelské rozhraní pro tisk náhledu.</span><span class="sxs-lookup"><span data-stu-id="53cc6-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="53cc6-105">Pokud chcete standardní uživatelské rozhraní, použijte ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog>; Přehled najdete v tématu [Přehled ovládacího prvku PrintPreviewDialog –](printpreviewdialog-control-overview-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="53cc6-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="53cc6-106">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="53cc6-106">Key Properties</span></span>  
 <span data-ttu-id="53cc6-107">Vlastnost klíče ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, ve kterém se nastaví náhled dokumentu.</span><span class="sxs-lookup"><span data-stu-id="53cc6-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="53cc6-108">Dokument musí být objekt <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="53cc6-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="53cc6-109">Přehled vytváření dokumentů pro tisk najdete v tématu [Přehled komponent PrintDocument](printdocument-component-overview-windows-forms.md) a [Podpora tisku model Windows Forms](../advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="53cc6-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="53cc6-110">Vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="53cc6-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="53cc6-111">Antialiasing může zobrazit hladší text, ale může také zpomalit zobrazení. Pokud ho chcete použít, nastavte vlastnost <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> na `true`.</span><span class="sxs-lookup"><span data-stu-id="53cc6-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53cc6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53cc6-112">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewControl>
- [<span data-ttu-id="53cc6-113">Přehled ovládacího prvku PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="53cc6-113">PrintPreviewDialog Control Overview</span></span>](printpreviewdialog-control-overview-windows-forms.md)
- [<span data-ttu-id="53cc6-114">Ovládací prvek PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="53cc6-114">PrintPreviewControl Control</span></span>](printpreviewcontrol-control-windows-forms.md)
- [<span data-ttu-id="53cc6-115">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="53cc6-115">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
