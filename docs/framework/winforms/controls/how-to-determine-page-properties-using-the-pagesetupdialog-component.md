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
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="570b6-102">Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="570b6-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="570b6-103">Komponenta [PageSetupDialog](pagesetupdialog-component-windows-forms.md) představuje uživateli možnosti rozložení, velikosti papíru a dalších možností rozložení stránky pro dokument.</span><span class="sxs-lookup"><span data-stu-id="570b6-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="570b6-104">Je třeba zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy – toto je dokument, který má být vytištěn.</span><span class="sxs-lookup"><span data-stu-id="570b6-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="570b6-105">Kromě toho musí mít uživatelé v počítači nainstalovanou tiskárnu, a to <xref:System.Windows.Forms.PageSetupDialog> buď místně, nebo prostřednictvím sítě, protože je to částečně způsob, jakým komponenta určuje volby formátování stránky prezentované uživateli.</span><span class="sxs-lookup"><span data-stu-id="570b6-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="570b6-106">Důležitým aspektem práce <xref:System.Windows.Forms.PageSetupDialog> s komponentou je, <xref:System.Drawing.Printing.PageSettings> jak spolupracuje s třídou.</span><span class="sxs-lookup"><span data-stu-id="570b6-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="570b6-107">Třída <xref:System.Drawing.Printing.PageSettings> se používá k určení nastavení, která mění způsob tisku stránky, například orientaci papíru, velikost stránky a okraje.</span><span class="sxs-lookup"><span data-stu-id="570b6-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="570b6-108">Každé z těchto nastavení je reprezentováno jako vlastnost třídy. <xref:System.Drawing.Printing.PageSettings></span><span class="sxs-lookup"><span data-stu-id="570b6-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="570b6-109">Třída <xref:System.Windows.Forms.PageSetupDialog> upraví tyto hodnoty vlastností pro danou <xref:System.Drawing.Printing.PageSettings> instanci třídy, která je <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> přidružena k dokumentu (a je reprezentována jako vlastnost).</span><span class="sxs-lookup"><span data-stu-id="570b6-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="570b6-110">Nastavení vlastností stránky pomocí komponenty PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="570b6-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="570b6-111">Pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody zobrazte dialogové okno <xref:System.Drawing.Printing.PrintDocument> s určením, které má být používáno.</span><span class="sxs-lookup"><span data-stu-id="570b6-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="570b6-112">V níže uvedeném <xref:System.Windows.Forms.Button> příkladu <xref:System.Windows.Forms.Control.Click> obslužná <xref:System.Windows.Forms.PageSetupDialog> rutina události ovládacího prvku otevře instanci komponenty.</span><span class="sxs-lookup"><span data-stu-id="570b6-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="570b6-113">Existující dokument je zadán <xref:System.Windows.Forms.PageSetupDialog.Document%2A> ve vlastnosti a <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> `false`jeho vlastnost je nastavena na .</span><span class="sxs-lookup"><span data-stu-id="570b6-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="570b6-114">Příklad předpokládá, že formulář <xref:System.Windows.Forms.Button> má <xref:System.Drawing.Printing.PrintDocument> ovládací `myDocument`prvek, <xref:System.Windows.Forms.PageSetupDialog> komponentu s názvem a komponentu.</span><span class="sxs-lookup"><span data-stu-id="570b6-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="570b6-115">(Visual C# a Visual C++) Umístěte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="570b6-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="570b6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="570b6-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="570b6-117">Postupy: Vytváření standardních tiskových úloh modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="570b6-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="570b6-118">PageSetupDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="570b6-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
