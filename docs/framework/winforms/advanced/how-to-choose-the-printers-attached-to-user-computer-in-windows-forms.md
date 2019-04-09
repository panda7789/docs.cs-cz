---
title: 'Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: bebb879020e6e45e77f109bf9c377b7322d5e8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184025"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a><span data-ttu-id="8f3c6-102">Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f3c6-102">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>
<span data-ttu-id="8f3c6-103">Uživatelé často chtějí vybrat tiskárnu jiné než výchozí tiskárna pro tisk.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="8f3c6-104">Můžete umožnit uživatelům si vybrat tiskárnu z aktuálně nainstalované pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="8f3c6-105">Prostřednictvím <xref:System.Windows.Forms.PrintDialog> komponenty, <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> komponenta je zachycena a umožňuje vybrat tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="8f3c6-106">V následujícím postupu je textový soubor vybraný které se mají vytisknout, použije se výchozí tiskárna.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="8f3c6-107"><xref:System.Windows.Forms.PrintDialog> Pak vytvoření instance třídy.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="8f3c6-108">Můžete vybrat tiskárnu a potom tisk souboru</span><span class="sxs-lookup"><span data-stu-id="8f3c6-108">To choose a printer and then print a file</span></span>  
  
1.  <span data-ttu-id="8f3c6-109">Vyberte tiskárny, kterou chcete použít pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="8f3c6-110">V následujícím příkladu kódu existují dvě události se zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="8f3c6-111">V první <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí, <xref:System.Windows.Forms.PrintDialog> je vytvořena instance třídy a jsou zachyceny tiskárny vybraných uživatelem <xref:System.Windows.Forms.DialogResult> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="8f3c6-112">V druhém případě <xref:System.Drawing.Printing.PrintDocument.PrintPage> událost <xref:System.Drawing.Printing.PrintDocument> komponentu, vytiskne se ukázkový dokument na tiskárně zadaná.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If   
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))          
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =   
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     <span data-ttu-id="8f3c6-113">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8f3c6-113">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8f3c6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f3c6-114">See also</span></span>

- [<span data-ttu-id="8f3c6-115">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8f3c6-115">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
