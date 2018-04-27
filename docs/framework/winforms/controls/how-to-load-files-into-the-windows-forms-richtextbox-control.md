---
title: 'Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox'
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
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27ddc78c16b04f067e83f799e8ccb275cebdeb14
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8b4bb-102">Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8b4bb-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="8b4bb-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení může zobrazit prostého textu, prostého textu ve formátu Unicode nebo soubor formátu formátovaného textu (RTF).</span><span class="sxs-lookup"><span data-stu-id="8b4bb-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="8b4bb-104">Chcete-li tak učinit, zavolejte <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="8b4bb-105">Můžete také <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu pro načtení dat z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="8b4bb-106">Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="8b4bb-107">Načtení souboru do ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8b4bb-107">To load a file into the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="8b4bb-108">Určete cestu k souboru otevřít pomocí <xref:System.Windows.Forms.OpenFileDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="8b4bb-109">Přehled najdete v tématu [OpenFileDialog – přehled komponenty](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8b4bb-109">For an overview, see [OpenFileDialog Component Overview](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="8b4bb-110">Volání <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> řízení, zadáte soubor načíst a volitelně typu souboru.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="8b4bb-111">V následujícím příkladu je soubor načíst převzat ze <xref:System.Windows.Forms.OpenFileDialog> součásti <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="8b4bb-112">Pokud jste volali metodu s názvem souboru jako argument pouze, bude považován za RTF typ souboru.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="8b4bb-113">Chcete-li určit jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="8b4bb-114">V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> komponenta se zobrazí při stisknutí tlačítka.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="8b4bb-115">Vybraný soubor je pak otevřít a zobrazit v <xref:System.Windows.Forms.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="8b4bb-116">Tento příklad předpokládá, že formulář obsahuje tlačítko,`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     <span data-ttu-id="8b4bb-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8b4bb-118">Tento proces spustit, vaše sestavení může vyžadovat úroveň oprávnění uděleno pomocí <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b4bb-119">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8b4bb-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="8b4bb-120">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8b4bb-120">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4bb-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b4bb-121">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="8b4bb-122">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8b4bb-122">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="8b4bb-123">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b4bb-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
