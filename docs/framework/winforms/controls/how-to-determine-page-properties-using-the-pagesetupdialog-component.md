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
ms.openlocfilehash: 7c65eb54bb95b9a20cd1e43f0d491af47985f2e0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329203"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="7126b-102">Postupy: Určení vlastností stránky pomocí komponenty PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="7126b-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="7126b-103">[PageSetupDialog](pagesetupdialog-component-windows-forms.md) součást se zobrazí rozložení, formát papíru a jiné možnosti rozložení stránky pro uživatele pro dokument.</span><span class="sxs-lookup"><span data-stu-id="7126b-103">The [PageSetupDialog](pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="7126b-104">Je třeba zadat instanci <xref:System.Drawing.Printing.PrintDocument> třídy – jedná o dokument, které se mají vytisknout.</span><span class="sxs-lookup"><span data-stu-id="7126b-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="7126b-105">Kromě toho uživatelé musí mít tiskárny nainstalované v počítači, místně nebo prostřednictvím sítě, protože je částečně jak <xref:System.Windows.Forms.PageSetupDialog> komponenty Určuje stránky se uživateli zobrazí možnosti formátování.</span><span class="sxs-lookup"><span data-stu-id="7126b-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="7126b-106">Důležitou součástí práce s <xref:System.Windows.Forms.PageSetupDialog> komponenta je, jak komunikuje se službou <xref:System.Drawing.Printing.PageSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="7126b-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="7126b-107"><xref:System.Drawing.Printing.PageSettings> Třída se používá k určení nastavení, které určuje způsob, jak na stránce budou zobrazeny, jako je orientace papíru, velikost stránky a okraje.</span><span class="sxs-lookup"><span data-stu-id="7126b-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="7126b-108">Každé z těchto nastavení je reprezentována jako vlastnost <xref:System.Drawing.Printing.PageSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="7126b-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="7126b-109"><xref:System.Windows.Forms.PageSetupDialog> Třídy změní hodnoty těchto vlastností pro danou instanci <xref:System.Drawing.Printing.PageSettings> třídy, který je přidružený dokument (a je vyjádřena jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> vlastnost).</span><span class="sxs-lookup"><span data-stu-id="7126b-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="7126b-110">Nastavení vlastností stránky pomocí komponenty PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="7126b-110">To set page properties using the PageSetupDialog component</span></span>  
  
1. <span data-ttu-id="7126b-111">Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu zadání <xref:System.Drawing.Printing.PrintDocument> používat.</span><span class="sxs-lookup"><span data-stu-id="7126b-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="7126b-112">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevírá instanci <xref:System.Windows.Forms.PageSetupDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7126b-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="7126b-113">Existující dokument je určen v <xref:System.Windows.Forms.PageSetupDialog.Document%2A> vlastnost a jeho <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="7126b-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="7126b-114">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PageSetupDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="7126b-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="7126b-115">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="7126b-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7126b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7126b-116">See also</span></span>

- <xref:System.Windows.Forms.PageSetupDialog>
- [<span data-ttu-id="7126b-117">Postupy: Vytváření standardních tiskových úloh v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7126b-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [<span data-ttu-id="7126b-118">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="7126b-118">PageSetupDialog Component</span></span>](pagesetupdialog-component-windows-forms.md)
