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
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Postupy: Zobrazení náhledu tisku ve formulářových aplikacích Windows
Pomocí ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> můžete uživatelům umožnit zobrazit dokument, často ještě předtím, než bude vytištěn.  
  
 K tomu je nutné zadat instanci třídy <xref:System.Drawing.Printing.PrintDocument>; dokument, který se má vytisknout Další informace o použití náhledu tisku s komponentou <xref:System.Drawing.Printing.PrintDocument> najdete v tématu [How to: Print in model Windows Forms using Print Preview](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
> Chcete-li použít ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> v době běhu, musí mít uživatelé na svém počítači nainstalovanou tiskárnu, a to buď místně, nebo prostřednictvím sítě, protože je částečně to, jak komponenta <xref:System.Windows.Forms.PrintPreviewDialog> určuje, jak bude dokument vypadat po vytištění.  
  
 Ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> používá třídu <xref:System.Drawing.Printing.PrinterSettings>. Kromě toho ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog> používá třídu <xref:System.Drawing.Printing.PageSettings>, stejně jako komponenta <xref:System.Windows.Forms.PrintPreviewDialog>. Tiskový dokument zadaný v vlastnosti <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> odkazuje na instance třídy <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> a ty se používají k vykreslení dokumentu v okně náhledu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Zobrazení stránek pomocí ovládacího prvku PrintPreviewDialog –  
  
- Použijte metodu <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> k zobrazení dialogového okna a určení <xref:System.Drawing.Printing.PrintDocument>, který se má použít.  
  
     V následujícím příkladu kódu obslužná rutina události <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button> otevře instanci ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>. Tiskového dokumentu je zadán ve vlastnosti <xref:System.Windows.Forms.PrintDialog.Document%2A>. V následujícím příkladu není zadán žádný dokument pro tisk.  
  
     Příklad vyžaduje, aby váš formulář měl ovládací prvek <xref:System.Windows.Forms.Button>, <xref:System.Drawing.Printing.PrintDocument> komponentu s názvem `myDocument`a ovládací prvek <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
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
  
     (Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také

- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
- [Ovládací prvek PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
