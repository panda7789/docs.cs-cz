---
title: "Postupy: volba tiskáren připojených k uživatele & č. 39; s počítači v systému Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec334ff65095e11855d706f445fda1d4b7ea1472
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-choose-the-printers-attached-to-a-user39s-computer-in-windows-forms"></a><span data-ttu-id="62b17-102">Postupy: volba tiskáren připojených k uživatele & č. 39; s počítači v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62b17-102">How to: Choose the Printers Attached to a User&#39;s Computer in Windows Forms</span></span>
<span data-ttu-id="62b17-103">Často uživatelé chtějí zvolte jiné než výchozí tiskárny pro tisk na tiskárnu.</span><span class="sxs-lookup"><span data-stu-id="62b17-103">Often, users want to choose a printer other than the default printer to print to.</span></span> <span data-ttu-id="62b17-104">Můžete povolit uživatelům zvolit některou tiskárnu aktuálně nainstalované pomocí <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="62b17-104">You can enable users to choose a printer from among those currently installed by using the <xref:System.Windows.Forms.PrintDialog> component.</span></span> <span data-ttu-id="62b17-105">Prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti, <xref:System.Windows.Forms.DialogResult> z <xref:System.Windows.Forms.PrintDialog> součásti bude zachycen a použit k výběru tiskárny.</span><span class="sxs-lookup"><span data-stu-id="62b17-105">Through the <xref:System.Windows.Forms.PrintDialog> component, the <xref:System.Windows.Forms.DialogResult> of the <xref:System.Windows.Forms.PrintDialog> component is captured and used to select the printer.</span></span>  
  
 <span data-ttu-id="62b17-106">V následujícím postupu je vybrán vytištěny do výchozí tiskárny do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="62b17-106">In the following procedure, a text file is selected to be printed to the default printer.</span></span> <span data-ttu-id="62b17-107"><xref:System.Windows.Forms.PrintDialog> Pak vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="62b17-107">The <xref:System.Windows.Forms.PrintDialog> class is then instantiated.</span></span>  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a><span data-ttu-id="62b17-108">Vybrat tiskárnu a pak vytištění souboru</span><span class="sxs-lookup"><span data-stu-id="62b17-108">To choose a printer and then print a file</span></span>  
  
1.  <span data-ttu-id="62b17-109">Vyberte tiskárny k použití pomocí <xref:System.Windows.Forms.PrintDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="62b17-109">Select the printer to be used using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
     <span data-ttu-id="62b17-110">V následujícím příkladu kódu jsou dvě události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="62b17-110">In the following code example, there are two events being handled.</span></span> <span data-ttu-id="62b17-111">V první <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí, <xref:System.Windows.Forms.PrintDialog> vytvoření instance třídy a je vybraný uživatelem tiskárny zachyceného <xref:System.Windows.Forms.DialogResult> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="62b17-111">In the first, a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event, the <xref:System.Windows.Forms.PrintDialog> class is instantiated and the printer selected by the user is captured in the <xref:System.Windows.Forms.DialogResult> property.</span></span>  
  
     <span data-ttu-id="62b17-112">V druhé události <xref:System.Drawing.Printing.PrintDocument.PrintPage> události <xref:System.Drawing.Printing.PrintDocument> součásti, dokument ukázka tisku tiskárně zadán.</span><span class="sxs-lookup"><span data-stu-id="62b17-112">In the second event, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event of the <xref:System.Drawing.Printing.PrintDocument> component, a sample document is printed to the printer specified.</span></span>  
  
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
  
     <span data-ttu-id="62b17-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="62b17-113">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62b17-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="62b17-114">See Also</span></span>  
 [<span data-ttu-id="62b17-115">Podpora tisku ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="62b17-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
