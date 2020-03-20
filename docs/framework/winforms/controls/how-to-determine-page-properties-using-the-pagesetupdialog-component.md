---
title: 'Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
ms.openlocfilehash: 8a015c199193dfd9c43bec53cc93cbf9dc201413
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142040"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog
Komponenta [PageSetupDialog](pagesetupdialog-component-windows-forms.md) představuje uživateli možnosti rozložení, velikosti papíru a dalších možností rozložení stránky pro dokument.  
  
 Je třeba zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy – toto je dokument, který má být vytištěn. Kromě toho musí mít uživatelé v počítači nainstalovanou tiskárnu, a to <xref:System.Windows.Forms.PageSetupDialog> buď místně, nebo prostřednictvím sítě, protože je to částečně způsob, jakým komponenta určuje volby formátování stránky prezentované uživateli.  
  
 Důležitým aspektem práce <xref:System.Windows.Forms.PageSetupDialog> s komponentou je, <xref:System.Drawing.Printing.PageSettings> jak spolupracuje s třídou. Třída <xref:System.Drawing.Printing.PageSettings> se používá k určení nastavení, která mění způsob tisku stránky, například orientaci papíru, velikost stránky a okraje. Každé z těchto nastavení je reprezentováno jako vlastnost třídy. <xref:System.Drawing.Printing.PageSettings> Třída <xref:System.Windows.Forms.PageSetupDialog> upraví tyto hodnoty vlastností pro danou <xref:System.Drawing.Printing.PageSettings> instanci třídy, která je <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> přidružena k dokumentu (a je reprezentována jako vlastnost).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Nastavení vlastností stránky pomocí komponenty PageSetupDialog  
  
1. Pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody zobrazte dialogové okno <xref:System.Drawing.Printing.PrintDocument> s určením, které má být používáno.  
  
     V níže uvedeném <xref:System.Windows.Forms.Button> příkladu <xref:System.Windows.Forms.Control.Click> obslužná <xref:System.Windows.Forms.PageSetupDialog> rutina události ovládacího prvku otevře instanci komponenty. Existující dokument je zadán <xref:System.Windows.Forms.PageSetupDialog.Document%2A> ve vlastnosti a <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> `false`jeho vlastnost je nastavena na .  
  
     Příklad předpokládá, že formulář <xref:System.Windows.Forms.Button> má <xref:System.Drawing.Printing.PrintDocument> ovládací `myDocument`prvek, <xref:System.Windows.Forms.PageSetupDialog> komponentu s názvem a komponentu.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       ' The print document 'myDocument' used below  
       ' is merely for an example.  
       'You will have to specify your own print document.  
       PageSetupDialog1.Document = myDocument  
       ' Sets the print document's color setting to false,  
       ' so that the page will not be printed in color.  
       PageSetupDialog1.Document.DefaultPageSettings.Color = False  
       PageSetupDialog1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // The print document 'myDocument' used below  
       // is merely for an example.  
       // You will have to specify your own print document.  
       pageSetupDialog1.Document = myDocument;  
       // Sets the print document's color setting to false,  
       // so that the page will not be printed in color.  
       pageSetupDialog1.Document.DefaultPageSettings.Color = false;  
       pageSetupDialog1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button1_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // The print document 'myDocument' used below  
          // is merely for an example.  
          // You will have to specify your own print document.  
          pageSetupDialog1->Document = myDocument;  
          // Sets the print document's color setting to false,  
          // so that the page will not be printed in color.  
          pageSetupDialog1->Document->DefaultPageSettings->Color = false;  
          pageSetupDialog1->ShowDialog();  
       }  
    ```  
  
     (Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PageSetupDialog>
- [Postupy: Vytváření standardních tiskových úloh modelu Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [PageSetupDialog – komponenta](pagesetupdialog-component-windows-forms.md)
