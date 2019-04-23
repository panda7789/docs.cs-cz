---
title: PrintPreviewControl – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122496"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="993e4-102">PrintPreviewControl – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="993e4-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="993e4-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> slouží k zobrazení [PrintDocument](printdocument-component-windows-forms.md) jak bude vypadat po vytištění.</span><span class="sxs-lookup"><span data-stu-id="993e4-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="993e4-104">Tento ovládací prvek nemá žádné tlačítka nebo další prvky uživatelského rozhraní, proto obvykle použijete <xref:System.Windows.Forms.PrintPreviewControl> pouze v případě, že chcete napsat vlastní náhled tisku uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="993e4-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="993e4-105">Pokud chcete, aby se standardní uživatelské rozhraní, použijte <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek; viz [printpreviewdialog – Přehled ovládacího prvku](printpreviewdialog-control-overview-windows-forms.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="993e4-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="993e4-106">Vlastnosti klíče</span><span class="sxs-lookup"><span data-stu-id="993e4-106">Key Properties</span></span>  
 <span data-ttu-id="993e4-107">Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, který nastaví dokumentu, který má být zobrazen.</span><span class="sxs-lookup"><span data-stu-id="993e4-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="993e4-108">Dokument musí být <xref:System.Drawing.Printing.PrintDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="993e4-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="993e4-109">Přehled vytváření dokumentů pro tisk, naleznete v tématu [PrintDocument – přehled komponenty](printdocument-component-overview-windows-forms.md) a [podpora Windows Forms tisk](../advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="993e4-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="993e4-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti určují počet stránek zobrazených vodorovně a svisle na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="993e4-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="993e4-111">Vyhlazení může zvýšit zobrazí hladší text, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="993e4-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993e4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="993e4-112">See also</span></span>

- <xref:System.Windows.Forms.PrintPreviewControl>
- [<span data-ttu-id="993e4-113">Přehled ovládacího prvku PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="993e4-113">PrintPreviewDialog Control Overview</span></span>](printpreviewdialog-control-overview-windows-forms.md)
- [<span data-ttu-id="993e4-114">Ovládací prvek PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="993e4-114">PrintPreviewControl Control</span></span>](printpreviewcontrol-control-windows-forms.md)
- [<span data-ttu-id="993e4-115">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="993e4-115">Dialog-Box Controls and Components</span></span>](dialog-box-controls-and-components-windows-forms.md)
