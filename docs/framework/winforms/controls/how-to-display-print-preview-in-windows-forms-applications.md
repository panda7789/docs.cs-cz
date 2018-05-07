---
title: 'Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows'
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
ms.openlocfilehash: 1c1291ea675d823fab3052b0fa365cb2d4c31088
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows
Můžete použít <xref:System.Windows.Forms.PrintPreviewDialog> řízení umožňuje uživatelům zobrazit dokumentu, často před je vytisknout.  
  
 K tomuto účelu, budete muset zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy; Toto je dokumentu, který má být vytisknout. Další informace o použití náhledu tisku s <xref:System.Drawing.Printing.PrintDocument> součást, najdete v části [postup: v systému Windows Forms pomocí náhledu tisku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku za běhu, uživatelé musí mít tiskárnu místně nebo přes síť s nainstalován v počítači, protože se jedná částečně jak <xref:System.Windows.Forms.PrintPreviewDialog> součást Určuje, jak bude vypadat dokument po vytištění.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Používá ovládací prvek <xref:System.Drawing.Printing.PrinterSettings> třídy. Kromě toho <xref:System.Windows.Forms.PrintPreviewDialog> používá ovládací prvek <xref:System.Drawing.Printing.PageSettings> třídu, stejně jako <xref:System.Windows.Forms.PrintPreviewDialog> komponenty dělají. Tisk dokumentu zadaného v <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> odkazuje vlastnost instance i <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a ty se používají k vykreslení dokumentu v okně náhledu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Chcete-li zobrazit stránky pomocí printpreviewdialog – ovládací prvek  
  
-   Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu určení <xref:System.Drawing.Printing.PrintDocument> používat.  
  
     V následujícím příkladu kódu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevře instanci <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Tisk dokumentu je uveden v <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost. V následujícím příkladu je zadána žádná tisku dokumentu.  
  
     Tento příklad vyžaduje, aby svého formuláře <xref:System.Windows.Forms.Button> řízení, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Komponenta PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
