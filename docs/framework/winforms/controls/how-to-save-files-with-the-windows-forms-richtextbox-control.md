---
title: Uložení souborů pomocí ovládacího prvku RichTextBox
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
ms.openlocfilehash: a87b93a53347aeba54f944b0f4c455aa272ea243
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744816"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="85bd7-102">Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="85bd7-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="85bd7-103">Ovládací prvek model Windows Forms <xref:System.Windows.Forms.RichTextBox> může zapisovat informace, které se zobrazí v jednom z několika formátů:</span><span class="sxs-lookup"><span data-stu-id="85bd7-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>

- <span data-ttu-id="85bd7-104">Prostý text</span><span class="sxs-lookup"><span data-stu-id="85bd7-104">Plain text</span></span>

- <span data-ttu-id="85bd7-105">Prostý text v kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="85bd7-105">Unicode plain text</span></span>

- <span data-ttu-id="85bd7-106">Rich Text Format (RTF)</span><span class="sxs-lookup"><span data-stu-id="85bd7-106">Rich-Text Format (RTF)</span></span>

- <span data-ttu-id="85bd7-107">RTF s mezerami místo objektů OLE</span><span class="sxs-lookup"><span data-stu-id="85bd7-107">RTF with spaces in place of OLE objects</span></span>

- <span data-ttu-id="85bd7-108">Prostý text s textovou reprezentací objektů OLE</span><span class="sxs-lookup"><span data-stu-id="85bd7-108">Plain text with a textual representation of OLE objects</span></span>

<span data-ttu-id="85bd7-109">Chcete-li uložit soubor, zavolejte metodu <xref:System.Windows.Forms.RichTextBox.SaveFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="85bd7-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="85bd7-110">Pomocí metody **SaveFile** můžete také ukládat data do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="85bd7-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="85bd7-111">Další informace najdete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="85bd7-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="85bd7-112">Uložení obsahu ovládacího prvku do souboru</span><span class="sxs-lookup"><span data-stu-id="85bd7-112">To save the contents of the control to a file</span></span>

1. <span data-ttu-id="85bd7-113">Určete cestu k souboru, který se má uložit.</span><span class="sxs-lookup"><span data-stu-id="85bd7-113">Determine the path of the file to be saved.</span></span>

    <span data-ttu-id="85bd7-114">K tomu v reálné aplikaci byste obvykle použili součást <xref:System.Windows.Forms.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="85bd7-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="85bd7-115">Přehled naleznete v tématu [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85bd7-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="85bd7-116">Zavolejte metodu <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> ovládacího prvku <xref:System.Windows.Forms.RichTextBox> a určete soubor, který se má uložit, a volitelně také typ souboru.</span><span class="sxs-lookup"><span data-stu-id="85bd7-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="85bd7-117">Pokud voláte metodu s názvem souboru jako s jediným argumentem, soubor bude uložen jako RTF.</span><span class="sxs-lookup"><span data-stu-id="85bd7-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="85bd7-118">Chcete-li zadat jiný typ souboru, zavolejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako svůj druhý argument.</span><span class="sxs-lookup"><span data-stu-id="85bd7-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="85bd7-119">V následujícím příkladu je cesta nastavená pro umístění souboru s bohatou čárkou ve složce **dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="85bd7-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="85bd7-120">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tuto složku.</span><span class="sxs-lookup"><span data-stu-id="85bd7-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="85bd7-121">Zvolíte-li toto umístění, mohou uživatelé s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="85bd7-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="85bd7-122">Následující příklad předpokládá, že formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="85bd7-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>

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
    > <span data-ttu-id="85bd7-123">Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="85bd7-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="85bd7-124">Pokud aplikace potřebuje vytvořit soubor, musí tato aplikace pro složku vytvořit přístup.</span><span class="sxs-lookup"><span data-stu-id="85bd7-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="85bd7-125">Oprávnění se nastavují pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="85bd7-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="85bd7-126">Pokud soubor už existuje, aplikace potřebuje jenom přístup pro zápis, což je menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="85bd7-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="85bd7-127">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a místo toho udělit přístup ke složce jenom přístup pro čtení jenom pro jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="85bd7-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="85bd7-128">Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.</span><span class="sxs-lookup"><span data-stu-id="85bd7-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

## <a name="see-also"></a><span data-ttu-id="85bd7-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85bd7-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="85bd7-130">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="85bd7-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="85bd7-131">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="85bd7-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
