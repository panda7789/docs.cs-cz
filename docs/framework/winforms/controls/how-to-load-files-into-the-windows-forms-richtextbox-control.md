---
title: Načtení souborů do ovládacího prvku RichTextBox
ms.date: 03/30/2017
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
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736296"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="15958-102">Postupy: Načtení souborů do ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="15958-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="15958-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> může zobrazit prostý text, prostý text v kódování Unicode nebo soubor RTF (Rich-Text-Format).</span><span class="sxs-lookup"><span data-stu-id="15958-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="15958-104">Uděláte to tak, že zavoláte metodu <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="15958-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="15958-105">K načtení dat z datového proudu můžete použít také metodu <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="15958-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="15958-106">Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="15958-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="15958-107">Načtení souboru do ovládacího prvku RichTextBox</span><span class="sxs-lookup"><span data-stu-id="15958-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="15958-108">Určete cestu k souboru, který se má otevřít, pomocí <xref:System.Windows.Forms.OpenFileDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="15958-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="15958-109">Přehled naleznete v tématu [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="15958-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="15958-110">Zavolejte metodu <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox>, určete soubor, který se má načíst, a volitelně také typ souboru.</span><span class="sxs-lookup"><span data-stu-id="15958-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="15958-111">V následujícím příkladu se soubor, který se má načíst, převezme z vlastnosti <xref:System.Windows.Forms.FileDialog.FileName%2A> <xref:System.Windows.Forms.OpenFileDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="15958-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="15958-112">Pokud zavoláte metodu s názvem souboru jako jeho jediným argumentem, typ souboru se bude považovat za RTF.</span><span class="sxs-lookup"><span data-stu-id="15958-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="15958-113">Chcete-li zadat jiný typ souboru, zavolejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako svůj druhý argument.</span><span class="sxs-lookup"><span data-stu-id="15958-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="15958-114">V následujícím příkladu je po kliknutí na tlačítko zobrazena součást <xref:System.Windows.Forms.OpenFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="15958-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="15958-115">Vybraný soubor je pak otevřen a zobrazen v ovládacím prvku <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="15958-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="15958-116">Tento příklad předpokládá, že formulář obsahuje tlačítko,`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="15958-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

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

    <span data-ttu-id="15958-117">(Vizuál C#, vizuál C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="15958-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="15958-118">Pro spuštění tohoto procesu vaše sestavení může vyžadovat úroveň oprávnění udělené třídou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="15958-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="15958-119">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="15958-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="15958-120">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="15958-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15958-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="15958-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="15958-122">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="15958-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="15958-123">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="15958-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
