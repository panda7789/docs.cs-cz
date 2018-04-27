---
title: 'Postupy: Otevírání souborů pomocí součásti OpenFileDialog'
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
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7da2c660f09da74c84d29459cf283a021ed12c99
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="34207-102">Postupy: Otevírání souborů pomocí součásti OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="34207-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="34207-103"><xref:System.Windows.Forms.OpenFileDialog> Součást umožňuje uživatelům procházet složky jejich počítače nebo všechny počítače v síti a vyberte jeden nebo více souborů otevřete.</span><span class="sxs-lookup"><span data-stu-id="34207-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="34207-104">Dialogové okno vrátí cestu a název souboru, vyberte v dialogovém okně vyberte uživatele.</span><span class="sxs-lookup"><span data-stu-id="34207-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="34207-105">Jakmile uživatel vybral soubor otevřít, existují dva přístupy mechanismu, který otevírání tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="34207-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="34207-106">Pokud dáváte přednost práci s datovými proudy souboru, můžete vytvořit instanci <xref:System.IO.StreamReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="34207-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="34207-107">Alternativně můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda otevřít vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="34207-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="34207-108">V prvním příkladu níže zahrnuje <xref:System.Security.Permissions.FileIOPermission> zkontrolujte oprávnění (jak je popsáno v "Zabezpečení poznámku" níže), ale dává vám přístup k názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="34207-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="34207-109">Tento postup můžete použít z místního počítače, intranetu a Internetu zóny.</span><span class="sxs-lookup"><span data-stu-id="34207-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="34207-110">Druhá metoda zajišťuje také <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění, ale je vhodnější pro aplikací do zóny intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="34207-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="34207-111">Otevřete soubor jako datový proud pomocí součásti OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="34207-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="34207-112">Zobrazení **otevřít soubor** dialogové okno a volání metody k otevření souboru vybraného uživatelem.</span><span class="sxs-lookup"><span data-stu-id="34207-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="34207-113">Jeden z přístupů je použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> má metoda zobrazit dialogové okno otevřít soubor a použít instanci systému <xref:System.IO.StreamReader> třída k otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="34207-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="34207-114">V příkladu níže používá <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události otevřete instanci <xref:System.Windows.Forms.OpenFileDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="34207-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="34207-115">Pokud je soubor zvolený a uživatel klikne na tlačítko **OK**, otevře se soubor vybraný v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="34207-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="34207-116">Obsah v tomto případě se zobrazí v okně se zprávou, stačí k zobrazení byl načten datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="34207-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="34207-117">Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="34207-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="34207-118">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="34207-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="34207-119">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="34207-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="34207-120">Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení a <xref:System.Windows.Forms.OpenFileDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="34207-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="34207-121">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="34207-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="34207-122">Další informace o čtení ze souboru datové proudy najdete v tématu <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="34207-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="34207-123">Otevřete soubor jako soubor pomocí součásti OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="34207-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="34207-124">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogových oken a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda k otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="34207-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="34207-125"><xref:System.Windows.Forms.OpenFileDialog> Součásti <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda vrátí počet bajtů, které tvoří soubor.</span><span class="sxs-lookup"><span data-stu-id="34207-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="34207-126">Tyto bajtů dát číst z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="34207-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="34207-127">V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> s filtrem "kurzoru", které uživateli umožňují zvolit pouze soubory s příponou názvu souboru je vytvořena instance komponenty`.cur`.</span><span class="sxs-lookup"><span data-stu-id="34207-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="34207-128">Pokud`.cur` je vybrán soubor, formuláře kurzor nastavený na vybrané kurzor.</span><span class="sxs-lookup"><span data-stu-id="34207-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="34207-129">K volání <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="34207-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="34207-130">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="34207-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="34207-131">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="34207-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="34207-132">Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="34207-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     <span data-ttu-id="34207-133">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="34207-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="34207-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="34207-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="34207-135">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="34207-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
