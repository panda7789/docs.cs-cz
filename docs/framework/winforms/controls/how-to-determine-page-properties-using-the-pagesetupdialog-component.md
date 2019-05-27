---
title: 'Postupy: Určení vlastností stránky pomocí komponenty PageSetupDialog'
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
ms.openlocfilehash: 306e0dbf7fb819d1214d7d5d93d335b5d2db75e6
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053621"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Postupy: Určení vlastností stránky pomocí komponenty PageSetupDialog
[PageSetupDialog](pagesetupdialog-component-windows-forms.md) součást se zobrazí rozložení, formát papíru a jiné možnosti rozložení stránky pro uživatele pro dokument.  
  
 Je třeba zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy – jedná o dokument, které se mají vytisknout. Kromě toho uživatelé musí mít tiskárny nainstalované v počítači, místně nebo prostřednictvím sítě, protože je částečně jak <xref:System.Windows.Forms.PageSetupDialog> komponenty Určuje stránky se uživateli zobrazí možnosti formátování.  
  
 Důležitou součástí práce s <xref:System.Windows.Forms.PageSetupDialog> komponenta je, jak komunikuje se službou <xref:System.Drawing.Printing.PageSettings> třídy. <xref:System.Drawing.Printing.PageSettings> Třída se používá k určení nastavení, které určuje způsob, jak na stránce budou zobrazeny, jako je orientace papíru, velikost stránky a okraje. Každé z těchto nastavení je reprezentována jako vlastnost <xref:System.Drawing.Printing.PageSettings> třídy. <xref:System.Windows.Forms.PageSetupDialog> Třídy změní hodnoty těchto vlastností pro danou instanci <xref:System.Drawing.Printing.PageSettings> třídy, který je přidružený dokument (a je vyjádřena jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> vlastnost).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Nastavení vlastností stránky pomocí komponenty PageSetupDialog  
  
1. Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu zadání <xref:System.Drawing.Printing.PrintDocument> používat.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevírá instanci <xref:System.Windows.Forms.PageSetupDialog> komponenty. Existující dokument je určen v <xref:System.Windows.Forms.PageSetupDialog.Document%2A> vlastnost a jeho <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> je nastavena na `false`.  
  
     Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PageSetupDialog> komponenty.  
  
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
  
     (Visual C# a vizuální C++) Umístěte následující kód do konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PageSetupDialog>
- [Postupy: Vytvoření tiskových úloh standardní Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Komponenta PageSetupDialog](pagesetupdialog-component-windows-forms.md)
