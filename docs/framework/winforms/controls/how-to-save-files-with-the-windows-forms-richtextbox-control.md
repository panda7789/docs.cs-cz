---
title: "Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox"
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
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fece6685c1ac71d6ddc152e25c22010e6d579c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="1c341-102">Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox</span><span class="sxs-lookup"><span data-stu-id="1c341-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="1c341-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení může zapsat informace se zobrazí v některém z formátů:</span><span class="sxs-lookup"><span data-stu-id="1c341-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="1c341-104">Prostý text</span><span class="sxs-lookup"><span data-stu-id="1c341-104">Plain text</span></span>  
  
-   <span data-ttu-id="1c341-105">Prostý text v kódu Unicode</span><span class="sxs-lookup"><span data-stu-id="1c341-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="1c341-106">RTF (Rich Text Format)</span><span class="sxs-lookup"><span data-stu-id="1c341-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="1c341-107">RTF prostory místo OLE – objekty</span><span class="sxs-lookup"><span data-stu-id="1c341-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="1c341-108">Ve formátu prostého textu s textovou reprezentaci OLE – objekty</span><span class="sxs-lookup"><span data-stu-id="1c341-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="1c341-109">Chcete-li uložit soubor, volejte <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1c341-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="1c341-110">Můžete také **SaveFile** metoda k uložení dat do datového proudu.</span><span class="sxs-lookup"><span data-stu-id="1c341-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="1c341-111">Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="1c341-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="1c341-112">Chcete uložit obsah ovládacího prvku do souboru</span><span class="sxs-lookup"><span data-stu-id="1c341-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="1c341-113">Určete cestu k souboru uložit.</span><span class="sxs-lookup"><span data-stu-id="1c341-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="1c341-114">K tomu v reálné aplikaci byste obvykle použili <xref:System.Windows.Forms.SaveFileDialog> součásti.</span><span class="sxs-lookup"><span data-stu-id="1c341-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="1c341-115">Přehled najdete v tématu [SaveFileDialog – přehled komponenty](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1c341-115">For an overview, see [SaveFileDialog Component Overview](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="1c341-116">Volání <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> řízení, soubor uložte a volitelně typu souboru.</span><span class="sxs-lookup"><span data-stu-id="1c341-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="1c341-117">Pokud jste volali metodu s názvem souboru jako argument pouze, uloží soubor ve formátu RTF.</span><span class="sxs-lookup"><span data-stu-id="1c341-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="1c341-118">Chcete-li určit jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako druhý argument.</span><span class="sxs-lookup"><span data-stu-id="1c341-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="1c341-119">V následujícím příkladu cesta pro umístění souboru formátovaného textu je nastavena **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="1c341-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="1c341-120">Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="1c341-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="1c341-121">Výběr toto umístění také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit.</span><span class="sxs-lookup"><span data-stu-id="1c341-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="1c341-122">Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="1c341-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
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
    >  <span data-ttu-id="1c341-123">Tento příklad vytvoří nový soubor, pokud soubor již neexistuje.</span><span class="sxs-lookup"><span data-stu-id="1c341-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1c341-124">Pokud aplikace potřebuje k vytvoření souboru, tuto aplikaci potřebuje vytvořit přístup ke složce.</span><span class="sxs-lookup"><span data-stu-id="1c341-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="1c341-125">Jsou oprávnění nastavena pomocí seznamů řízení přístupu.</span><span class="sxs-lookup"><span data-stu-id="1c341-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="1c341-126">Pokud soubor již existuje, aplikace potřebuje pouze k zápisu, a menší oprávnění.</span><span class="sxs-lookup"><span data-stu-id="1c341-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="1c341-127">Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a jenom udělit přístup pro čtení do jednoho souboru, než vytvořit přístupu pro složku.</span><span class="sxs-lookup"><span data-stu-id="1c341-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="1c341-128">Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.</span><span class="sxs-lookup"><span data-stu-id="1c341-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c341-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c341-129">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="1c341-130">Ovládací prvek RichTextBox</span><span class="sxs-lookup"><span data-stu-id="1c341-130">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="1c341-131">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1c341-131">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
