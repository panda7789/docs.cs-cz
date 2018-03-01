---
title: "PrintPreviewControl – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a><span data-ttu-id="efb48-102">PrintPreviewControl – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="efb48-102">PrintPreviewControl Control Overview (Windows Forms)</span></span>
<span data-ttu-id="efb48-103">Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> se používá k zobrazení [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) jak se zobrazí při tisku.</span><span class="sxs-lookup"><span data-stu-id="efb48-103">The Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> is used to display a [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) as it will appear when printed.</span></span> <span data-ttu-id="efb48-104">Tento ovládací prvek má žádné tlačítka nebo další prvky uživatelského rozhraní, takže obvykle použijete <xref:System.Windows.Forms.PrintPreviewControl> pouze v případě, že chcete napsat vlastní náhledu uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="efb48-104">This control has no buttons or other user interface elements, so typically you use the <xref:System.Windows.Forms.PrintPreviewControl> only if you wish to write your own print-preview user interface.</span></span> <span data-ttu-id="efb48-105">Pokud chcete standardní uživatelské rozhraní, použijte <xref:System.Windows.Forms.PrintPreviewDialog> řízení; viz [printpreviewdialog – Přehled ovládacího prvku](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="efb48-105">If you want the standard user interface, use a <xref:System.Windows.Forms.PrintPreviewDialog> control; see [PrintPreviewDialog Control Overview](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) for an overview.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="efb48-106">Klíčové vlastnosti</span><span class="sxs-lookup"><span data-stu-id="efb48-106">Key Properties</span></span>  
 <span data-ttu-id="efb48-107">Klíčová vlastnost ovládacího prvku je <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, která nastaví dokument, který chcete zobrazit jejich náhled.</span><span class="sxs-lookup"><span data-stu-id="efb48-107">The control's key property is <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, which sets the document to be previewed.</span></span> <span data-ttu-id="efb48-108">Musí být dokument <xref:System.Drawing.Printing.PrintDocument> objektu.</span><span class="sxs-lookup"><span data-stu-id="efb48-108">The document must be a <xref:System.Drawing.Printing.PrintDocument> object.</span></span> <span data-ttu-id="efb48-109">Přehled vytváření dokumentů pro tisk, najdete v části [PrintDocument – přehled komponenty](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) a [podpora prostředí Windows Forms tiskových](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span><span class="sxs-lookup"><span data-stu-id="efb48-109">For an overview of creating documents for printing, see [PrintDocument Component Overview](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) and [Windows Forms Print Support](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md).</span></span> <span data-ttu-id="efb48-110"><xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> a <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> vlastnosti určit, kolik stránek se zobrazí vodorovně a svisle na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="efb48-110">The <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> and <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> properties determine the number of pages displayed horizontally and vertically on the control.</span></span> <span data-ttu-id="efb48-111">Vyhlazení může zvýšit text zobrazí hladší, ale také může být pomalejší; zobrazení Chcete-li použít, nastavte <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="efb48-111">Antialiasing can make the text appear smoother, but it can also make the display slower; to use it, set the <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb48-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="efb48-112">See Also</span></span>  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [<span data-ttu-id="efb48-113">Přehled ovládacího prvku PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="efb48-113">PrintPreviewDialog Control Overview</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [<span data-ttu-id="efb48-114">Ovládací prvek PrintPreviewControl</span><span class="sxs-lookup"><span data-stu-id="efb48-114">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [<span data-ttu-id="efb48-115">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="efb48-115">Dialog-Box Controls and Components</span></span>](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
