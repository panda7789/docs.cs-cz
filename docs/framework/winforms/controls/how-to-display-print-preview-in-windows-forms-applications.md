---
title: 'Postupy: Zobrazení náhledu tisku ve Windows Forms aplikací'
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
ms.openlocfilehash: 13510086edb13ff54f5551296c1b64c51873f649
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715357"
---
# <a name="how-to-display-print-preview-in-windows-forms-applications"></a>Postupy: Zobrazení náhledu tisku ve Windows Forms aplikací
Můžete použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládací prvek umožňující uživatelům často zobrazení dokumentu, než které se mají vytisknout.  
  
 K tomuto účelu, budete muset zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy; jedná o dokument, které se mají vytisknout. Další informace o použití náhledu tisku s <xref:System.Drawing.Printing.PrintDocument> komponenty, naleznete v tématu [jak: Tisk ve Windows Forms pomocí náhledu tisku](../advanced/how-to-print-in-windows-forms-using-print-preview.md).  
  
> [!NOTE]
>  Použít <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku za běhu, uživatelé musí mít tiskárny nainstalované v počítači, místně nebo prostřednictvím sítě, protože je částečně jak <xref:System.Windows.Forms.PrintPreviewDialog> komponenty Určuje, jak bude dokument vypadat po vytištění.  
  
 <xref:System.Windows.Forms.PrintPreviewDialog> Používá ovládací prvek <xref:System.Drawing.Printing.PrinterSettings> třídy. Kromě toho <xref:System.Windows.Forms.PrintPreviewDialog> používá ovládací prvek <xref:System.Drawing.Printing.PageSettings> třídu, stejně jako <xref:System.Windows.Forms.PrintPreviewDialog> komponenty dělají. Vytištěný dokument podle <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku <xref:System.Windows.Forms.PrintPreviewControl.Document%2A> vlastnost odkazuje na oba výskyty <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a ty se používají k vykreslení dokumentu v okně verze preview.  
  
### <a name="to-view-pages-using-the-printpreviewdialog-control"></a>Chcete-li zobrazit stránky s využitím printpreviewdialog – ovládací prvek  
  
-   Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu zadání <xref:System.Drawing.Printing.PrintDocument> používat.  
  
     V následujícím příkladu kódu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevírá instanci <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku. Vytištěný dokument je určen v <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost. V následujícím příkladu je zadána žádná vytištěný dokument.  
  
     V příkladu vyžaduje, že váš formulář má <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Komponenta PrintDocument](printdocument-component-windows-forms.md)
- [Ovládací prvek PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms](../index.md)
