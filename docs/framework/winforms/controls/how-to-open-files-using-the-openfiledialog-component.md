---
title: 'Postupy: Otevírání souborů pomocí komponenty OpenFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678808"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="8e4fa-102">Postupy: Otevírání souborů pomocí komponenty OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8e4fa-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="8e4fa-103"><xref:System.Windows.Forms.OpenFileDialog> Komponenta umožňuje uživatelům procházet složky jejich počítač nebo všechny počítače v síti a vyberte jeden nebo více souborů otevřete.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="8e4fa-104">Dialogové okno vrátí cestu a název souboru v dialogovém okně vyberte uživatele.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="8e4fa-105">Jakmile uživatel vybral soubor otevřít, se používají dva přístupy mechanismu, který otevírání tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="8e4fa-106">Pokud budete chtít pracovat s datové proudy souborů, můžete vytvořit instanci <xref:System.IO.StreamReader> třídy.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="8e4fa-107">Alternativně můžete použít <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda otevřít vybraný soubor.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="8e4fa-108">V prvním příkladu níže se zahrnuje <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění (jak je popsáno v "Zabezpečení poznámku" níže), ale dává vám přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="8e4fa-109">Tento postup můžete použít z místního počítače, intranetu a Internetu zóny.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="8e4fa-110">Druhá metoda také provádí <xref:System.Security.Permissions.FileIOPermission> kontrola oprávnění, ale je vhodnější pro aplikace v zóně intranetu nebo Internetu.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="8e4fa-111">Pro otevření souboru jako datový proud pomocí komponenty OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8e4fa-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="8e4fa-112">Zobrazení **otevřít soubor** dialogové okno a volání metody otevřít soubor vybraný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="8e4fa-113">Jedním z přístupů je použít <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogového okna otevřete soubor a použít instanci <xref:System.IO.StreamReader> třídy k otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="8e4fa-114">V příkladu níže použití <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události otevřete instance <xref:System.Windows.Forms.OpenFileDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="8e4fa-115">Pokud je soubor zvolené a uživatel klikne na tlačítko **OK**, otevře se soubor vybrané v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="8e4fa-116">V takovém případě obsah se zobrazí v okně se zprávou, pouze k znázornění přečetla datový proud souboru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8e4fa-117">Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8e4fa-118">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="8e4fa-119">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8e4fa-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="8e4fa-120">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku a <xref:System.Windows.Forms.OpenFileDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="8e4fa-121">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8e4fa-122">Další informace o čtení ze souborů datových proudů, naleznete v tématu <xref:System.IO.FileStream.BeginRead%2A> a <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="8e4fa-123">Pro otevření souboru jako souboru pomocí komponenty OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8e4fa-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="8e4fa-124">Použití <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodu pro zobrazení dialogových oken a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody k otevření souboru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="8e4fa-125"><xref:System.Windows.Forms.OpenFileDialog> Komponenty <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda vrátí počet bajtů, které ho tvoří.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="8e4fa-126">Tyto bajtů umožňují čtení z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="8e4fa-127">V následujícím příkladu <xref:System.Windows.Forms.OpenFileDialog> s filtrem "kurzor", které uživateli umožňují vybrat pouze soubory s příponou názvu souboru je vytvořena instance komponenty`.cur`.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="8e4fa-128">Pokud`.cur` je vybrán soubor, kurzor formuláře je nastavena na vybrané kurzoru.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8e4fa-129">Volání <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8e4fa-130">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku, protože nedostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="8e4fa-131">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8e4fa-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="8e4fa-132">Příklad předpokládá, že váš formulář má <xref:System.Windows.Forms.Button> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
     <span data-ttu-id="8e4fa-133">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="8e4fa-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8e4fa-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e4fa-134">See also</span></span>
- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="8e4fa-135">Komponenta OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="8e4fa-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
