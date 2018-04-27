---
title: 'Postupy: Ukládání souborů pomocí součásti SaveFileDialog'
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
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cace4dcd9aa5eb5d46579044905bbf2e5d755b66
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="c990b-102">Postupy: Ukládání souborů pomocí součásti SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c990b-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="c990b-103"><xref:System.Windows.Forms.SaveFileDialog> Součást umožňuje uživatelům procházet systému souborů a vyberte soubory uložit.</span><span class="sxs-lookup"><span data-stu-id="c990b-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="c990b-104">Dialogové okno vrátí cestu a název souboru, který uživatel vybral v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="c990b-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="c990b-105">Ale musíte napsat kód, který ve skutečnosti zapisovat soubory na disk.</span><span class="sxs-lookup"><span data-stu-id="c990b-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="c990b-106">Uložte soubor pomocí součásti SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c990b-106">To save a file using the SaveFileDialog component</span></span>  
  
-   <span data-ttu-id="c990b-107">Zobrazení **uložit soubor** dialogové okno a uložte soubor vybraný uživatelem volání metody.</span><span class="sxs-lookup"><span data-stu-id="c990b-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="c990b-108">Použití <xref:System.Windows.Forms.SaveFileDialog> součásti <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metoda k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="c990b-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="c990b-109">Tato metoda vám <xref:System.IO.Stream> objekt můžete zapisovat.</span><span class="sxs-lookup"><span data-stu-id="c990b-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="c990b-110">V příkladu níže používá <xref:System.Windows.Forms.DialogResult> vlastnost k získání názvu souboru a <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="c990b-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="c990b-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda vám dává datového proudu pro zápis souboru.</span><span class="sxs-lookup"><span data-stu-id="c990b-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="c990b-112">V následujícím příkladu je <xref:System.Windows.Forms.Button> ovládacího prvku s bitovou kopií přiřazen.</span><span class="sxs-lookup"><span data-stu-id="c990b-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="c990b-113">Po kliknutí na tlačítko <xref:System.Windows.Forms.SaveFileDialog> s filtrem, která umožňuje soubory .gif typu, .jpeg a .bmp je vytvořena instance komponenty.</span><span class="sxs-lookup"><span data-stu-id="c990b-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="c990b-114">Pokud je vybrán soubor tohoto typu v dialogovém okně Uložit soubor, je obrázek na tlačítko Uložit.</span><span class="sxs-lookup"><span data-stu-id="c990b-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c990b-115">Pro získání nebo nastavení <xref:System.Windows.Forms.FileDialog.FileName%2A> vlastnost, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="c990b-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c990b-116">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c990b-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="c990b-117">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c990b-117">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="c990b-118">Příklad předpokládá, že má formulář <xref:System.Windows.Forms.Button> řízení s jeho <xref:System.Windows.Forms.ButtonBase.Image%2A> vlastností nastavenou na soubor typu .gif, .jpeg nebo BMP.</span><span class="sxs-lookup"><span data-stu-id="c990b-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c990b-119"><xref:System.Windows.Forms.FileDialog> Třídy <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> vlastnost (které, z důvodu dědičnosti, je součástí <xref:System.Windows.Forms.SaveFileDialog> třída) používá indexu se základem jedna.</span><span class="sxs-lookup"><span data-stu-id="c990b-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="c990b-120">To je důležité, pokud vytváříte kód k uložení dat v konkrétním formátu (například ukládání soubor ve formátu prostého textu a binární formát).</span><span class="sxs-lookup"><span data-stu-id="c990b-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="c990b-121">Tato vlastnost je umístěná v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c990b-121">This property is featured in the example below.</span></span>  
  
    ```vb  
    Private Sub Button2_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button2.Click  
       ' Displays a SaveFileDialog so the user can save the Image  
       ' assigned to Button2.  
       Dim saveFileDialog1 As New SaveFileDialog()  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"  
       saveFileDialog1.Title = "Save an Image File"  
       saveFileDialog1.ShowDialog()  
  
       ' If the file name is not an empty string open it for saving.  
       If saveFileDialog1.FileName <> "" Then  
          ' Saves the Image via a FileStream created by the OpenFile method.  
          Dim fs As System.IO.FileStream = Ctype _  
             (saveFileDialog1.OpenFile(), System.IO.FileStream)  
          ' Saves the Image in the appropriate ImageFormat based upon the  
          ' file type selected in the dialog box.  
          ' NOTE that the FilterIndex property is one-based.  
          Select Case saveFileDialog1.FilterIndex  
             Case 1  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Jpeg)  
  
             Case 2  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Bmp)  
  
             Case 3  
                Me.button2.Image.Save(fs, _  
                   System.Drawing.Imaging.ImageFormat.Gif)  
           End Select  
  
           fs.Close()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button2_Click(object sender, System.EventArgs e)  
    {  
       // Displays a SaveFileDialog so the user can save the Image  
       // assigned to Button2.  
       SaveFileDialog saveFileDialog1 = new SaveFileDialog();  
       saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
       saveFileDialog1.Title = "Save an Image File";  
       saveFileDialog1.ShowDialog();  
  
       // If the file name is not an empty string open it for saving.  
       if(saveFileDialog1.FileName != "")  
       {  
          // Saves the Image via a FileStream created by the OpenFile method.  
          System.IO.FileStream fs =   
             (System.IO.FileStream)saveFileDialog1.OpenFile();  
          // Saves the Image in the appropriate ImageFormat based upon the  
          // File type selected in the dialog box.  
          // NOTE that the FilterIndex property is one-based.  
          switch(saveFileDialog1.FilterIndex)  
          {  
             case 1 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Jpeg);  
             break;  
  
             case 2 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Bmp);  
             break;  
  
             case 3 :   
             this.button2.Image.Save(fs,   
                System.Drawing.Imaging.ImageFormat.Gif);  
             break;  
          }  
  
       fs.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void button2_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays a SaveFileDialog so the user can save the Image  
          // assigned to Button2.  
          SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();  
          saveFileDialog1->Filter =   
             "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";  
          saveFileDialog1->Title = "Save an Image File";  
          saveFileDialog1->ShowDialog();  
          // If the file name is not an empty string, open it for saving.  
          if(saveFileDialog1->FileName != "")  
          {  
             // Saves the Image through a FileStream created by  
             // the OpenFile method.  
             System::IO::FileStream ^ fs =   
                safe_cast\<System::IO::FileStream*>(  
                saveFileDialog1->OpenFile());  
             // Saves the Image in the appropriate ImageFormat based on  
             // the file type selected in the dialog box.  
             // Note that the FilterIndex property is one based.  
             switch(saveFileDialog1->FilterIndex)  
             {  
                case 1 :  
                   this->button2->Image->Save(fs,  
                      System::Drawing::Imaging::ImageFormat::Jpeg);  
                   break;  
                case 2 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Bmp);  
                   break;  
                case 3 :  
                   this->button2->Image->Save(fs,   
                      System::Drawing::Imaging::ImageFormat::Gif);  
                   break;  
             }  
          fs->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="c990b-122">(Visual C# a [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) vložte následující kód v konstruktoru formuláře k registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c990b-122">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="c990b-123">Další informace o vytváření souborů datových proudů najdete v tématu <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="c990b-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c990b-124">Některé ovládací prvky, jako například <xref:System.Windows.Forms.RichTextBox> řídit, máte možnost ukládat soubory.</span><span class="sxs-lookup"><span data-stu-id="c990b-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="c990b-125">Další informace najdete v části "SaveFileDialog – komponenta" technického článku MSDN Online Library z [nezbytné kód pro Windows Forms – dialogová](http://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="c990b-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c990b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c990b-126">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="c990b-127">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="c990b-127">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
