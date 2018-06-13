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
ms.openlocfilehash: 4b1acef216e4f8eca078d47a8cde87fb8f95ee0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532724"
---
# <a name="how-to-determine-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="93074-102">Postupy: Určení vlastností stránky pomocí součásti PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="93074-102">How to: Determine Page Properties Using the PageSetupDialog Component</span></span>
<span data-ttu-id="93074-103">[PageSetupDialog –](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) součást uvede rozložení, velikost papíru a další možnosti rozložení stránky pro uživatele pro dokument.</span><span class="sxs-lookup"><span data-stu-id="93074-103">The [PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) component presents layout, paper size, and other page layout choices to the user for a document.</span></span>  
  
 <span data-ttu-id="93074-104">Musíte zadat instanci <xref:System.Drawing.Printing.PrintDocument> – třída – Toto je dokumentu, který má být vytisknout.</span><span class="sxs-lookup"><span data-stu-id="93074-104">You need to specify an instance of the <xref:System.Drawing.Printing.PrintDocument> class—this is the document to be printed.</span></span> <span data-ttu-id="93074-105">Kromě toho uživatelé musí mít tiskárnu místně nebo přes síť s nainstalován v počítači, protože se jedná částečně jak <xref:System.Windows.Forms.PageSetupDialog> součást určuje formátování volby uživateli stránky.</span><span class="sxs-lookup"><span data-stu-id="93074-105">Additionally, users must have a printer installed on their computer, either locally or through a network, as this is partly how the <xref:System.Windows.Forms.PageSetupDialog> component determines the page formatting choices presented to the user.</span></span>  
  
 <span data-ttu-id="93074-106">Důležitým aspektem práce <xref:System.Windows.Forms.PageSetupDialog> součást je, jak pracuje s <xref:System.Drawing.Printing.PageSettings> – třída.</span><span class="sxs-lookup"><span data-stu-id="93074-106">An important aspect of working with the <xref:System.Windows.Forms.PageSetupDialog> component is how it interacts with the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="93074-107"><xref:System.Drawing.Printing.PageSettings> Třída se používá k určení nastavení, které určuje způsob, jak na stránce budou vytištěny, jako je například orientace papíru, velikosti stránky a pravého okraje.</span><span class="sxs-lookup"><span data-stu-id="93074-107">The <xref:System.Drawing.Printing.PageSettings> class is used to specify settings that modify the way a page will be printed, such as paper orientation, the size of the page, and the margins.</span></span> <span data-ttu-id="93074-108">Každé z těchto nastavení je reprezentován jako vlastnost <xref:System.Drawing.Printing.PageSettings> třídy.</span><span class="sxs-lookup"><span data-stu-id="93074-108">Each of these settings is represented as a property of the <xref:System.Drawing.Printing.PageSettings> class.</span></span> <span data-ttu-id="93074-109"><xref:System.Windows.Forms.PageSetupDialog> Třída upraví tyto hodnoty vlastností pro dané instanci systému <xref:System.Drawing.Printing.PageSettings> třídu, která souvisí s dokumentu (a je reprezentována jako <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> vlastnosti).</span><span class="sxs-lookup"><span data-stu-id="93074-109">The <xref:System.Windows.Forms.PageSetupDialog> class modifies these property values for a given instance of the <xref:System.Drawing.Printing.PageSettings> class that is associated with the document (and is represented as a <xref:System.Drawing.Printing.PrintDocument.DefaultPageSettings%2A> property).</span></span>  
  
### <a name="to-set-page-properties-using-the-pagesetupdialog-component"></a><span data-ttu-id="93074-110">Nastavení vlastností stránky pomocí součásti PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="93074-110">To set page properties using the PageSetupDialog component</span></span>  
  
1.  <span data-ttu-id="93074-111">Použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogu určení <xref:System.Drawing.Printing.PrintDocument> používat.</span><span class="sxs-lookup"><span data-stu-id="93074-111">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box, specifying the <xref:System.Drawing.Printing.PrintDocument> to use.</span></span>  
  
     <span data-ttu-id="93074-112">V následujícím příkladu <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevře instanci <xref:System.Windows.Forms.PageSetupDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="93074-112">In the example below, the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler opens an instance of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span> <span data-ttu-id="93074-113">Stávající dokument je uveden v <xref:System.Windows.Forms.PageSetupDialog.Document%2A> vlastnost a jeho <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> je nastavena na `false`.</span><span class="sxs-lookup"><span data-stu-id="93074-113">An existing document is specified in the <xref:System.Windows.Forms.PageSetupDialog.Document%2A> property, and its <xref:System.Drawing.Printing.PageSettings.Color%2A?displayProperty=nameWithType> property is set to `false`.</span></span>  
  
     <span data-ttu-id="93074-114">Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení, <xref:System.Drawing.Printing.PrintDocument> součást s názvem `myDocument`a <xref:System.Windows.Forms.PageSetupDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="93074-114">The example assumes your form has a <xref:System.Windows.Forms.Button> control, a <xref:System.Drawing.Printing.PrintDocument> component named `myDocument`, and a <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="93074-115">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="93074-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew   
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="93074-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="93074-116">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="93074-117">Postupy: Vytváření standardních tiskových úloh modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93074-117">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="93074-118">Komponenta PageSetupDialog</span><span class="sxs-lookup"><span data-stu-id="93074-118">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
