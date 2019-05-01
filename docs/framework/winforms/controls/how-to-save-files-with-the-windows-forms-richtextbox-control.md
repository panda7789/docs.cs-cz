---
title: 'Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 4784ddd563ccec0f7e6271700781ee1b5d3ac105
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013319"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="722d4-102">Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="722d4-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="722d4-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek lze zapsat informace se zobrazí v jednom z několika formátů:</span><span class="sxs-lookup"><span data-stu-id="722d4-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
- <span data-ttu-id="722d4-104">Prostý text</span><span class="sxs-lookup"><span data-stu-id="722d4-104">Plain text</span></span>  
  
- <span data-ttu-id="722d4-105">Kódování Unicode ve formátu prostého textu</span><span class="sxs-lookup"><span data-stu-id="722d4-105">Unicode plain text</span></span>  
  
- <span data-ttu-id="722d4-106">Rich-Text Format (RTF)</span><span class="sxs-lookup"><span data-stu-id="722d4-106">Rich-Text Format (RTF)</span></span>  
  
- <span data-ttu-id="722d4-107">RTF prostory místo objekty OLE</span><span class="sxs-lookup"><span data-stu-id="722d4-107">RTF with spaces in place of OLE objects</span></span>  
  
- <span data-ttu-id="722d4-108">Prostý text s textovou reprezentaci řetězce objekty OLE</span><span class="sxs-lookup"><span data-stu-id="722d4-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="722d4-109">Chcete-li uložit soubor, zavolejte <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="722d4-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="722d4-110">Můžete také použít **SaveFile** metoda k ukládání dat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="722d4-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="722d4-111">Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="722d4-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="722d4-112">Chcete uložit obsah ovládacího prvku do souboru</span><span class="sxs-lookup"><span data-stu-id="722d4-112">To save the contents of the control to a file</span></span>  
  
1. <span data-ttu-id="722d4-113">Určete cestu k souboru, který se má uložit.</span><span class="sxs-lookup"><span data-stu-id="722d4-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="722d4-114">K tomu v reálné aplikaci byste obvykle použili <xref:System.Windows.Forms.SaveFileDialog> komponenty.</span><span class="sxs-lookup"><span data-stu-id="722d4-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="722d4-115">Přehled najdete v tématu [SaveFileDialog – přehled komponenty](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="722d4-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="722d4-116">Volání <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> ovládací prvek, pro uložení souboru a volitelně typu souboru.</span><span class="sxs-lookup"><span data-stu-id="722d4-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="722d4-117">Pokud jste volali metodu s názvem souboru jako její jediný argument, soubor se uloží ve formátu RTF.</span><span class="sxs-lookup"><span data-stu-id="722d4-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="722d4-118">Chcete-li zadat jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčet jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="722d4-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="722d4-119">V následujícím příkladu nastavena cesta pro umístění souboru formátovaného textu je **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="722d4-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="722d4-120">Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="722d4-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="722d4-121">Výběrem tohoto umístění také umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="722d4-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="722d4-122">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="722d4-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="722d4-123">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="722d4-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="722d4-124">Pokud aplikace potřebuje k vytvoření souboru, aplikace potřebuje vytvořit přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="722d4-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="722d4-125">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="722d4-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="722d4-126">Pokud soubor již existuje, aplikace potřebuje pouze přístup pro zápis, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="722d4-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="722d4-127">Kde je to možné, je bezpečnější vytvořit soubor při nasazení a jenom udělit přístup pro čtení do jednoho souboru, ne vytvořit přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="722d4-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="722d4-128">Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="722d4-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722d4-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="722d4-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="722d4-130">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="722d4-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="722d4-131">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="722d4-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
