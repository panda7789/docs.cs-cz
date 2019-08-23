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
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Postupy: Zobrazení náhledu tisku v aplikacích Windows Forms
Pomocí <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku můžete uživatelům umožnit zobrazit dokument, často ještě předtím, než bude vytištěn.  
  
 K tomu je nutné zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy; jedná se o dokument, který se má vytisknout. Další informace o použití náhledu tisku s <xref:System.Drawing.Printing.PrintDocument> komponentou najdete v tématu [How to: Tisk v model Windows Forms pomocí náhledu](../advanced/how-to-print-in-windows-forms-using-print-preview.md)tisku.  
  
> [!NOTE]
> Chcete-li <xref:System.Windows.Forms.PrintPreviewDialog> použít ovládací prvek v době běhu, musí mít uživatelé na svém počítači nainstalovanou tiskárnu, a to buď místně, nebo prostřednictvím sítě, protože tato <xref:System.Windows.Forms.PrintPreviewDialog> součást Určuje, jak bude dokument vypadat po vytištění.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Ovládací prvek<xref:System.Drawing.Printing.PrinterSettings> používá třídu. Kromě toho <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek <xref:System.Drawing.Printing.PageSettings> používá <xref:System.Windows.Forms.PrintPreviewDialog> třídu, stejně jako komponenta. <xref:System.Windows.Forms.PrintPreviewDialog> Tiskový dokument zadaný ve <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> vlastnosti ovládacího prvku odkazuje <xref:System.Drawing.Printing.PrinterSettings> na instance třídy a <xref:System.Drawing.Printing.PageSettings> , a slouží k vykreslení dokumentu v okně náhledu.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Zobrazení stránek pomocí ovládacího prvku PrintPreviewDialog –  
  
- Použijte metodu k zobrazení dialogového okna a <xref:System.Drawing.Printing.PrintDocument> určení, které má být použito. <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> kódu obslužná rutina <xref:System.Windows.Forms.Control.Click> události ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog> otevře instanci ovládacího prvku. Tisk dokumentu je zadán ve <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnosti. V následujícím příkladu není zadán žádný dokument pro tisk.  
  
     Příklad vyžaduje, <xref:System.Windows.Forms.Button> aby formulář měl ovládací prvek <xref:System.Drawing.Printing.PrintDocument> , <xref:System.Windows.Forms.PrintPreviewDialog> komponentu s názvem `myDocument`a ovládací prvek.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
- [Ovládací prvek PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
