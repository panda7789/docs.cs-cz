---
title: 'Postupy: Zvolte složky s komponentou Windows Forms FolderBrowserDialog'
ms.date: 03/30/2017
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
ms.openlocfilehash: ea5fdc9708d8e896eb66fa42f64cac672baff08b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724554"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="e6383-102">Postupy: Zvolte složky s komponentou Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="e6383-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="e6383-103">Často v rámci aplikace Windows, které vytvoříte, budete muset vyzvat uživatele, vyberte složku, většina často budou sadu souborů.</span><span class="sxs-lookup"><span data-stu-id="e6383-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="e6383-104">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> komponenta umožňuje snadno provést tuto úlohu.</span><span class="sxs-lookup"><span data-stu-id="e6383-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="e6383-105">Chcete-li zvolit složky s FolderBrowserDialog – komponenta</span><span class="sxs-lookup"><span data-stu-id="e6383-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="e6383-106">V postupu, zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> komponenty <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnosti naleznete v tématu Jak bylo ukončeno dialogových oken a získání hodnoty <xref:System.Windows.Forms.FolderBrowserDialog> komponenty <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e6383-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="e6383-107">Pokud je nutné do složky sady úplně nahoře, který se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která přebírá členem <xref:System.Environment.SpecialFolder> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e6383-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="e6383-108">Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnost, která určuje, textový řetězec, který se zobrazí v horní části stromu zobrazení prohlížeč složek.</span><span class="sxs-lookup"><span data-stu-id="e6383-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="e6383-109">V následujícím příkladu <xref:System.Windows.Forms.FolderBrowserDialog> komponenty slouží k výběru složky, podobně jako při vytvoření projektu v sadě Visual Studio a vyzváni k výběru pro uložte ho do složky.</span><span class="sxs-lookup"><span data-stu-id="e6383-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="e6383-110">V tomto příkladu název složky se následně zobrazí <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="e6383-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="e6383-111">Je vhodné umístit umístění upravitelné oblasti, jako například <xref:System.Windows.Forms.TextBox> řídit, takže uživatelé mohou upravovat jejich výběr v případě chyby nebo jiné problémy.</span><span class="sxs-lookup"><span data-stu-id="e6383-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="e6383-112">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponenty a <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e6383-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
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
    >  <span data-ttu-id="e6383-113">Pro tuto třídu použít, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastnost, která je součástí sady <xref:System.Security.Permissions.FileIOPermissionAccess> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e6383-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="e6383-114">Pokud používáte v kontextu částečným vztahem důvěryhodnosti, procesu může vyvolat výjimku z důvodu dostatečná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e6383-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="e6383-115">Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e6383-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="e6383-116">Informace o tom, jak uložit soubory, naleznete v tématu [jak: Ukládání souborů pomocí součásti SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="e6383-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6383-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6383-117">See also</span></span>
- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="e6383-118">Přehled komponenty FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e6383-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="e6383-119">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="e6383-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
