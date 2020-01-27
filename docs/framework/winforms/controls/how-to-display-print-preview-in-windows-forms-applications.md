---
title: Zobrazení náhledu tisku v aplikacích model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print preview [Windows Forms], displaying
- printing [Windows Forms], print preview
- examples [Windows Forms], print preview
ms.assetid: e394134c-0886-4517-bd8d-edc4a3749eb5
ms.openlocfilehash: ac02339ad86e491cd047dcd4b0c8841374b3bb2e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745566"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="38ebf-102">Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows</span><span class="sxs-lookup"><span data-stu-id="38ebf-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="38ebf-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> můžete uživatelům umožnit zobrazit dokument, často ještě předtím, než bude vytištěn.</span><span class="sxs-lookup"><span data-stu-id="38ebf-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="38ebf-104">K tomu je nutné zadat instanci třídy <xref:System.Drawing.Printing.PrintDocument>; dokument, který se má vytisknout</span><span class="sxs-lookup"><span data-stu-id="38ebf-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="38ebf-105">Další informace o použití náhledu tisku s komponentou <xref:System.Drawing.Printing.PrintDocument> najdete v tématu [How to: Print in model Windows Forms using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span><span class="sxs-lookup"><span data-stu-id="38ebf-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38ebf-106">Chcete-li použít ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> v době běhu, musí mít uživatelé na svém počítači nainstalovanou tiskárnu, a to buď místně, nebo prostřednictvím sítě, protože je částečně to, jak komponenta <xref:System.Windows.Forms.PrintPreviewDialog> určuje, jak bude dokument vypadat po vytištění.</span><span class="sxs-lookup"><span data-stu-id="38ebf-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="38ebf-107">Ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> používá třídu <xref:System.Drawing.Printing.PrinterSettings>.</span><span class="sxs-lookup"><span data-stu-id="38ebf-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="38ebf-108">Kromě toho ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> používá třídu <xref:System.Drawing.Printing.PageSettings>, stejně jako komponenta <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="38ebf-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="38ebf-109">Tiskový dokument zadaný v vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> odkazuje na instance třídy <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> a ty se používají k vykreslení dokumentu v okně náhledu.</span><span class="sxs-lookup"><span data-stu-id="38ebf-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="38ebf-110">Zobrazení stránek pomocí ovládacího prvku PrintPreviewDialog –</span><span class="sxs-lookup"><span data-stu-id="38ebf-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="38ebf-111">Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna a určení <xref:System.Drawing.Printing.PrintDocument>, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="38ebf-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="38ebf-112">V následujícím příkladu kódu obslužná rutina události <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button> otevře instanci ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="38ebf-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="38ebf-113">Tiskového dokumentu je zadán ve vlastnosti <xref:System.Windows.Forms.PrintDialog.Document%2A>.</span><span class="sxs-lookup"><span data-stu-id="38ebf-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="38ebf-114">V následujícím příkladu není zadán žádný dokument pro tisk.</span><span class="sxs-lookup"><span data-stu-id="38ebf-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="38ebf-115">Příklad vyžaduje, aby váš formulář měl ovládací prvek <xref:System.Windows.Forms.Button>, <xref:System.Drawing.Printing.PrintDocument> komponentu s názvem `myDocument`a ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog>.</span><span class="sxs-lookup"><span data-stu-id="38ebf-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="38ebf-116">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="38ebf-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="38ebf-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38ebf-117">See also</span></span>

- [<span data-ttu-id="38ebf-118">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="38ebf-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="38ebf-119">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="38ebf-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="38ebf-120">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38ebf-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="38ebf-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38ebf-121">Windows Forms</span></span>](../index.md)
