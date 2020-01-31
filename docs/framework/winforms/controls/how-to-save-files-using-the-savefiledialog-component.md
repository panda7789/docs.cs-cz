---
title: 'Postupy: Ukládání souborů pomocí součásti SaveFileDialog'
ms.date: 03/30/2017
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
ms.openlocfilehash: 32de7f7e38195271e179d4fae3884b7a39f37c45
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868080"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="9568e-102">Postupy: Ukládání souborů pomocí součásti SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="9568e-102">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="9568e-103">Komponenta <xref:System.Windows.Forms.SaveFileDialog> umožňuje uživatelům procházet systém souborů a vybírat soubory, které mají být uloženy.</span><span class="sxs-lookup"><span data-stu-id="9568e-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="9568e-104">Dialogové okno vrátí cestu a název souboru, který uživatel vybral v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="9568e-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="9568e-105">Je však nutné napsat kód, který bude ve skutečnosti zapisovat soubory na disk.</span><span class="sxs-lookup"><span data-stu-id="9568e-105">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="9568e-106">Uložení souboru pomocí komponenty SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="9568e-106">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="9568e-107">Zobrazte dialogové okno **Uložit soubor** a voláním metody uložte soubor vybraný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9568e-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="9568e-108">Soubor uložte pomocí <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody <xref:System.Windows.Forms.SaveFileDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="9568e-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="9568e-109">Tato metoda poskytuje objekt <xref:System.IO.Stream>, do kterého lze zapisovat.</span><span class="sxs-lookup"><span data-stu-id="9568e-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="9568e-110">Následující příklad používá vlastnost <xref:System.Windows.Forms.DialogResult> k získání názvu souboru a metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> k uložení souboru.</span><span class="sxs-lookup"><span data-stu-id="9568e-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="9568e-111">Metoda <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> poskytuje datový proud, do kterého se má soubor zapsat.</span><span class="sxs-lookup"><span data-stu-id="9568e-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="9568e-112">V následujícím příkladu je k dispozici ovládací prvek <xref:System.Windows.Forms.Button> s přiřazenou obrázkem.</span><span class="sxs-lookup"><span data-stu-id="9568e-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="9568e-113">Po kliknutí na tlačítko se vytvoří instance <xref:System.Windows.Forms.SaveFileDialog> s filtrem, který umožňuje soubory typu. gif,. jpeg a. bmp.</span><span class="sxs-lookup"><span data-stu-id="9568e-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="9568e-114">Pokud je vybrán soubor tohoto typu v dialogovém okně Uložit soubor, je obrázek tlačítka uložen.</span><span class="sxs-lookup"><span data-stu-id="9568e-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9568e-115">Chcete-li získat nebo nastavit vlastnost <xref:System.Windows.Forms.FileDialog.FileName%2A>, sestavení vyžaduje úroveň oprávnění udělené třídou <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9568e-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9568e-116">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9568e-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="9568e-117">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="9568e-117">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="9568e-118">V příkladu se předpokládá, že má formulář <xref:System.Windows.Forms.Button> ovládací prvek s vlastností <xref:System.Windows.Forms.ButtonBase.Image%2A> nastavenou na soubor typu. gif,. jpeg nebo. bmp.</span><span class="sxs-lookup"><span data-stu-id="9568e-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9568e-119">Vlastnost <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> třídy <xref:System.Windows.Forms.FileDialog> (která z důvodu dědičnosti je součástí třídy <xref:System.Windows.Forms.SaveFileDialog>) používá index založený na jednom.</span><span class="sxs-lookup"><span data-stu-id="9568e-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="9568e-120">To je důležité, pokud píšete kód pro uložení dat v určitém formátu (například ukládání souboru v prostém textu versus v binárním formátu).</span><span class="sxs-lookup"><span data-stu-id="9568e-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="9568e-121">Tato vlastnost je vybraná v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9568e-121">This property is featured in the example below.</span></span>

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

  <span data-ttu-id="9568e-122">(Vizuální C# a vizuální C++) Vložte následující kód do konstruktoru formuláře pro registraci obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="9568e-122">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="9568e-123">Další informace o zápisu datových proudů souborů najdete v tématu <xref:System.IO.FileStream.BeginWrite%2A> a <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="9568e-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="9568e-124">Některé ovládací prvky, například ovládací prvek <xref:System.Windows.Forms.RichTextBox>, mají možnost ukládat soubory.</span><span class="sxs-lookup"><span data-stu-id="9568e-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="9568e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9568e-125">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="9568e-126">Komponenta SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="9568e-126">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
