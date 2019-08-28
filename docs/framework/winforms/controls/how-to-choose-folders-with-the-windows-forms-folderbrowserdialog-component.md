---
title: 'Postupy: Výběr složek pomocí komponenty Windows Forms FolderBrowserDialog'
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
ms.openlocfilehash: fc19ea466f535f783d3b0537a973ce41c223902d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046138"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="37e9f-102">Postupy: Výběr složek pomocí komponenty Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="37e9f-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="37e9f-103">V rámci aplikací systému Windows, které vytvoříte, budete často muset vyzvat uživatele k výběru složky, nejčastěji k uložení sady souborů.</span><span class="sxs-lookup"><span data-stu-id="37e9f-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="37e9f-104">Tato součást <xref:System.Windows.Forms.FolderBrowserDialog> umožňuje snadnou akci provádět pomocí model Windows Forms komponenty.</span><span class="sxs-lookup"><span data-stu-id="37e9f-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="37e9f-105">Výběr složek pomocí komponenty FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="37e9f-105">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="37e9f-106">V <xref:System.Windows.Forms.FolderBrowserDialog> proceduře zkontrolujte <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnost komponenty a podívejte se, jak se dialogové okno zavřelo, a <xref:System.Windows.Forms.FolderBrowserDialog> Získejte <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> hodnotu vlastnosti komponenty.</span><span class="sxs-lookup"><span data-stu-id="37e9f-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="37e9f-107">Pokud potřebujete nastavit složku nejvyšší úrovně, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která převezme člena <xref:System.Environment.SpecialFolder> výčtu.</span><span class="sxs-lookup"><span data-stu-id="37e9f-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="37e9f-108">Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnost, která určuje textový řetězec, který se zobrazí v horní části stromového zobrazení prohlížeče složky.</span><span class="sxs-lookup"><span data-stu-id="37e9f-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="37e9f-109">V následujícím <xref:System.Windows.Forms.FolderBrowserDialog> příkladu se komponenta používá k výběru složky, podobně jako při vytváření projektu v aplikaci Visual Studio, a zobrazí se výzva k výběru složky pro uložení.</span><span class="sxs-lookup"><span data-stu-id="37e9f-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="37e9f-110">V tomto příkladu se název složky zobrazí v <xref:System.Windows.Forms.TextBox> ovládacím prvku ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="37e9f-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="37e9f-111">Je vhodné umístit umístění do upravitelné oblasti, <xref:System.Windows.Forms.TextBox> jako je například ovládací prvek, aby si uživatelé mohli upravit svůj výběr v případě chyby nebo jiných problémů.</span><span class="sxs-lookup"><span data-stu-id="37e9f-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="37e9f-112">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponentou <xref:System.Windows.Forms.TextBox> a ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="37e9f-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="37e9f-113">Chcete-li použít tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastností, která je součástí <xref:System.Security.Permissions.FileIOPermissionAccess> výčtu.</span><span class="sxs-lookup"><span data-stu-id="37e9f-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="37e9f-114">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="37e9f-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="37e9f-115">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="37e9f-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="37e9f-116">Informace o tom, jak ukládat soubory, najdete [v tématu How to: Uložte soubory pomocí komponenty](how-to-save-files-using-the-savefiledialog-component.md)SaveFileDialog.</span><span class="sxs-lookup"><span data-stu-id="37e9f-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="37e9f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37e9f-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="37e9f-118">Přehled komponenty FolderBrowserDialog (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="37e9f-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="37e9f-119">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="37e9f-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
