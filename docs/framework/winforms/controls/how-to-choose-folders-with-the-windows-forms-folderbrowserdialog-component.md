---
title: "Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog"
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
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de41d5664c2481032dffe213a52779834338ca2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="eb775-102">Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="eb775-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="eb775-103">V rámci aplikace systému Windows, které vytvoříte, často, bude mít vyzve uživatele, vyberte složku, většina často k uložení sady souborů.</span><span class="sxs-lookup"><span data-stu-id="eb775-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="eb775-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> součást umožňuje snadno dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="eb775-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="eb775-105">Chcete-li zvolit složky s FolderBrowserDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="eb775-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="eb775-106">V postupu, zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> součásti <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnosti chcete zobrazit, jak bylo ukončeno dialogové okno a získat hodnotu <xref:System.Windows.Forms.FolderBrowserDialog> součásti <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eb775-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="eb775-107">Pokud budete potřebovat sadu nejvyšší úrovni složky, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která přebírá členem <xref:System.Environment.SpecialFolder> výčtu.</span><span class="sxs-lookup"><span data-stu-id="eb775-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="eb775-108">Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnosti, která určuje také textový řetězec, který se zobrazí v horní části stromovém zobrazení složky prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="eb775-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="eb775-109">V následujícím příkladu <xref:System.Windows.Forms.FolderBrowserDialog> součást slouží k výběru složky, podobně jako při vytvoření projektu v sadě Visual Studio a vyzváni k výběru složku pro uložení v.</span><span class="sxs-lookup"><span data-stu-id="eb775-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="eb775-110">V tomto příkladu se následně zobrazí název složky v <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="eb775-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="eb775-111">Je vhodné umístit umístění upravitelné oblast, například <xref:System.Windows.Forms.TextBox> řídit, tak, aby uživatelé mohou upravovat jejich výběr v případě chyby nebo jiných problémů.</span><span class="sxs-lookup"><span data-stu-id="eb775-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="eb775-112">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> součásti a <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb775-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="eb775-113">Pokud chcete používat tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastnost, která je součástí z <xref:System.Security.Permissions.FileIOPermissionAccess> – výčet.</span><span class="sxs-lookup"><span data-stu-id="eb775-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="eb775-114">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="eb775-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="eb775-115">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="eb775-115">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="eb775-116">Informace o tom, jak ukládat soubory najdete v tématu [postupy: ukládání souborů pomocí součásti SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="eb775-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb775-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb775-117">See Also</span></span>  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [<span data-ttu-id="eb775-118">Přehled komponenty FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="eb775-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [<span data-ttu-id="eb775-119">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="eb775-119">FolderBrowserDialog Component</span></span>](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
