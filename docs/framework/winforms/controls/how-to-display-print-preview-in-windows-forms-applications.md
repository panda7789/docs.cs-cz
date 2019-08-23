---
title: 'Postupy: Zobrazení náhledu tisku v aplikacích Windows Forms'
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
ms.openlocfilehash: 8252906de9a574f49617609a4cb08a1e8aa6a992
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929011"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a><span data-ttu-id="25e81-102">Postupy: Zobrazení náhledu tisku v aplikacích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25e81-102">How to: Display Print Preview in Windows Forms Applications</span></span>
<span data-ttu-id="25e81-103">Pomocí <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku můžete uživatelům umožnit zobrazit dokument, často ještě předtím, než bude vytištěn.</span><span class="sxs-lookup"><span data-stu-id="25e81-103">You can use the <xref:System.Windows.Forms.PrintPreviewDialog> control to enable users to display a document, often before it is to be printed.</span></span>  
  
 <span data-ttu-id="25e81-104">K tomu je nutné zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy; jedná se o dokument, který se má vytisknout.</span><span class="sxs-lookup"><span data-stu-id="25e81-104">To do this, you need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class; this is the document to be printed.</span></span> <span data-ttu-id="25e81-105">Další informace o použití náhledu tisku s <xref:System.Drawing.Printing.PrintDocument> komponentou najdete v tématu [How to: Tisk v model Windows Forms pomocí náhledu](../advanced/how-to-print-in-windows-forms-using-print-preview.md)tisku.</span><span class="sxs-lookup"><span data-stu-id="25e81-105">For more information about using print preview with the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print in Windows Forms Using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25e81-106">Chcete-li <xref:System.Windows.Forms.PrintPreviewDialog> použít ovládací prvek v době běhu, musí mít uživatelé na svém počítači nainstalovanou tiskárnu, a to buď místně, nebo prostřednictvím sítě, protože tato <xref:System.Windows.Forms.PrintPreviewDialog> součást Určuje, jak bude dokument vypadat po vytištění.</span><span class="sxs-lookup"><span data-stu-id="25e81-106">To use the <xref:System.Windows.Forms.PrintPreviewDialog> control at run time, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PrintPreviewDialog> component determines how a document will look when printed.</span></span>  
  
 <span data-ttu-id="25e81-107"><xref:System.Windows.Forms.PrintPreviewDialog> Ovládací prvek<xref:System.Drawing.Printing.PrinterSettings> používá třídu.</span><span class="sxs-lookup"><span data-stu-id="25e81-107">The <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span> <span data-ttu-id="25e81-108">Kromě toho <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek <xref:System.Drawing.Printing.PageSettings> používá <xref:System.Windows.Forms.PrintPreviewDialog> třídu, stejně jako komponenta.</span><span class="sxs-lookup"><span data-stu-id="25e81-108">Additionally, the <xref:System.Windows.Forms.PrintPreviewDialog> control uses the <xref:System.Drawing.Printing.PageSettings> class, just as the <xref:System.Windows.Forms.PrintPreviewDialog> component does.</span></span> <span data-ttu-id="25e81-109"><xref:System.Windows.Forms.PrintPreviewDialog> Tiskový dokument zadaný ve <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> vlastnosti ovládacího prvku odkazuje <xref:System.Drawing.Printing.PrinterSettings> na instance třídy a <xref:System.Drawing.Printing.PageSettings> , a slouží k vykreslení dokumentu v okně náhledu.</span><span class="sxs-lookup"><span data-stu-id="25e81-109">The print document specified in the <xref:System.Windows.Forms.PrintPreviewDialog> control's <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> property refers to instances of both the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and these are used to render the document in the preview window.</span></span>  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a><span data-ttu-id="25e81-110">Zobrazení stránek pomocí ovládacího prvku PrintPreviewDialog –</span><span class="sxs-lookup"><span data-stu-id="25e81-110">To view pages using the PrintPreviewDialog control</span></span>  
  
- <span data-ttu-id="25e81-111">Použijte metodu k zobrazení dialogového okna a <xref:System.Drawing.Printing.PrintDocument> určení, které má být použito. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A></span><span class="sxs-lookup"><span data-stu-id="25e81-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="25e81-112">V následujícím příkladu <xref:System.Windows.Forms.Button> kódu obslužná rutina <xref:System.Windows.Forms.Control.Click> události ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> otevře instanci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="25e81-112">In the following code example, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="25e81-113">Tisk dokumentu je zadán ve <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="25e81-113">The print document is specified in the <xref:System.Windows.Forms.PrintDialog.Document%2A> property.</span></span> <span data-ttu-id="25e81-114">V následujícím příkladu není zadán žádný dokument pro tisk.</span><span class="sxs-lookup"><span data-stu-id="25e81-114">In the example below, no print document is specified.</span></span>  
  
     <span data-ttu-id="25e81-115">Příklad vyžaduje, <xref:System.Windows.Forms.Button> aby formulář měl ovládací prvek <xref:System.Drawing.Printing.PrintDocument> , <xref:System.Windows.Forms.PrintPreviewDialog> komponentu s názvem `myDocument`a ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="25e81-115">The example requires that your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
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
  
     <span data-ttu-id="25e81-116">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="25e81-116">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="25e81-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25e81-117">See also</span></span>

- [<span data-ttu-id="25e81-118">Komponenta PrintDocument</span><span class="sxs-lookup"><span data-stu-id="25e81-118">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
- [<span data-ttu-id="25e81-119">Ovládací prvek PrintPreviewDialog</span><span class="sxs-lookup"><span data-stu-id="25e81-119">PrintPreviewDialog Control</span></span>](printpreviewdialog-control-windows-forms.md)
- [<span data-ttu-id="25e81-120">Podpora tisku v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25e81-120">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="25e81-121">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25e81-121">Windows Forms</span></span>](../index.md)
