---
title: "Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e705575b8c3acdcc3d92b985c59b60e7310dce7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="1cf07-102">Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="1cf07-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="1cf07-103">Můžete použít <xref:System.Windows.Forms.PrintPreviewDialog> řízení umožňuje uživatelům zobrazit dokumentu, často před je vytisknout.</span><span class="sxs-lookup"><span data-stu-id="1cf07-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="1cf07-104">K tomuto účelu, budete muset zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy; Toto je dokumentu, který má být vytisknout.</span><span class="sxs-lookup"><span data-stu-id="1cf07-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="1cf07-105">Další informace o použití náhledu tisku s <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postup: v systému Windows Forms pomocí náhledu tisku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="1cf07-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1cf07-106">Použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku za běhu, uživatelé musí mít tiskárnu místně nebo přes síť s nainstalován v počítači, protože se jedná částečně jak <xref:System.Windows.Forms.PrintPreviewDialog> součást Určuje, jak bude vypadat dokument po vytištění.</span><span class="sxs-lookup"><span data-stu-id="1cf07-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="1cf07-107"><xref:System.Windows.Forms.PrintPreviewDialog> Používá ovládací prvek <xref:System.Drawing.Printing.PrinterSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="1cf07-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="1cf07-108">Kromě toho <xref:System.Windows.Forms.PrintPreviewDialog> používá ovládací prvek <xref:System.Drawing.Printing.PageSettings> třídu, stejně jako <xref:System.Windows.Forms.PrintPreviewDialog> komponenty dělají.</span><span class="sxs-lookup"><span data-stu-id="1cf07-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="1cf07-109">Tisk dokumentu zadaného v <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> odkazuje vlastnost instance i <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a ty se používají k vykreslení dokumentu v okně náhledu.</span><span class="sxs-lookup"><span data-stu-id="1cf07-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="1cf07-110">Chcete-li zobrazit stránky pomocí printpreviewdialog – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1cf07-110">To view pages using the PrintPreviewDialog control</span></span>  
  
-   <span data-ttu-id="1cf07-111">Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu určení <xref:System.Drawing.Printing.PrintDocument> používat.</span><span class="sxs-lookup"><span data-stu-id="1cf07-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="1cf07-112">V následujícím příkladu kódu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevře instanci <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cf07-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="1cf07-113">Tisk dokumentu je uveden v <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1cf07-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="1cf07-114">V následujícím příkladu je zadána žádná tisku dokumentu.</span><span class="sxs-lookup"><span data-stu-id="1cf07-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="1cf07-115">Tento příklad vyžaduje, aby svého formuláře <xref:System.Windows.Forms.Button> řízení, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1cf07-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       ' You will have to specify your own print document.  
       PrintPreviewDialog1.Document = myDocument  
       PrintPreviewDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       printPreviewDialog1.Document = myDocument;  
       printPreviewDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          printPreviewDialog1->Document = myDocument;  
          printPreviewDialog1->ShowDialog();  
       }  
    ```  
  
     <span data-ttu-id="1cf07-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1cf07-116">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1cf07-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cf07-117">See Also</span></span>  
 [<span data-ttu-id="1cf07-118">PrintDocument – komponenta</span><span class="sxs-lookup"><span data-stu-id="1cf07-118">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [<span data-ttu-id="1cf07-119">Printpreviewdialog – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1cf07-119">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="1cf07-120">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cf07-120">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="1cf07-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1cf07-121">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
