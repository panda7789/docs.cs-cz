---
title: 'Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- page properties
- page setup
- PageSetupDialog component
ms.assetid: 6dae05bc-c0fd-4357-bb93-841a1631d98f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52ef02ccfe6586f89adabb30187aa48e5fe87349
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a>Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog
[PageSetupDialog –](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) součást uvede rozložení, velikost papíru a další možnosti rozložení stránky pro uživatele pro dokument.  
  
 Musíte zadat instanci <xref:System.Drawing.Printing.PrintDocument> – třída – Toto je dokumentu, který má být vytisknout. Kromě toho uživatelé musí mít tiskárnu místně nebo přes síť s nainstalován v počítači, protože se jedná částečně jak <xref:System.Windows.Forms.PageSetupDialog> součást určuje formátování volby uživateli stránky.  
  
 Důležitým aspektem práce <xref:System.Windows.Forms.PageSetupDialog> součást je, jak pracuje s <xref:System.Drawing.Printing.PageSettings> – třída. <xref:System.Drawing.Printing.PageSettings> Třída se používá k určení nastavení, které určuje způsob, jak na stránce budou vytištěny, jako je například orientace papíru, velikosti stránky a pravého okraje. Každé z těchto nastavení je reprezentován jako vlastnost <xref:System.Drawing.Printing.PageSettings> třídy. <xref:System.Windows.Forms.PageSetupDialog> Třída upraví tyto hodnoty vlastností pro dané instanci systému <xref:System.Drawing.Printing.PageSettings> třídu, která souvisí s dokumentu (a je reprezentována jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> vlastnosti).  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a>Nastavení vlastností stránky pomocí součásti PageSetupDialog  
  
1.  Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu určení <xref:System.Drawing.Printing.PrintDocument> používat.  
  
     V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevře instanci <xref:System.Windows.Forms.PageSetupDialog> součásti. Stávající dokument je uveden v <xref:System.Windows.Forms.PageSetupDialog.Document%2A> vlastnost a jeho <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> je nastavena na `false`.  
  
     Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PageSetupDialog> součásti.  
  
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
  
     (Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [Postupy: Vytváření standardních tiskových úloh modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Komponenta PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
