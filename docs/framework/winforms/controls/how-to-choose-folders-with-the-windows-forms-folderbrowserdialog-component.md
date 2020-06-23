---
title: Výběr složek s komponentou FolderBrowserDialog
description: Naučte se používat komponentu model Windows Forms FolderBrowserDialog v aplikacích pro Windows, které vytvoříte pro vyzvat uživatele k výběru složky.
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
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903672"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="c4e04-103">Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="c4e04-103">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="c4e04-104">V rámci aplikací systému Windows, které vytvoříte, budete často muset vyzvat uživatele k výběru složky, nejčastěji k uložení sady souborů.</span><span class="sxs-lookup"><span data-stu-id="c4e04-104">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="c4e04-105"><xref:System.Windows.Forms.FolderBrowserDialog>Tato součást umožňuje snadnou akci provádět pomocí model Windows Forms komponenty.</span><span class="sxs-lookup"><span data-stu-id="c4e04-105">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="c4e04-106">Výběr složek pomocí komponenty FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="c4e04-106">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="c4e04-107">V proceduře zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnost komponenty a podívejte se, jak se dialogové okno zavřelo, a získejte hodnotu <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> Vlastnosti komponenty.</span><span class="sxs-lookup"><span data-stu-id="c4e04-107">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="c4e04-108">Pokud potřebujete nastavit složku nejvyšší úrovně, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která převezme člena <xref:System.Environment.SpecialFolder> výčtu.</span><span class="sxs-lookup"><span data-stu-id="c4e04-108">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="c4e04-109">Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnost, která určuje textový řetězec, který se zobrazí v horní části stromového zobrazení prohlížeče složky.</span><span class="sxs-lookup"><span data-stu-id="c4e04-109">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="c4e04-110">V následujícím příkladu se <xref:System.Windows.Forms.FolderBrowserDialog> komponenta používá k výběru složky, podobně jako při vytváření projektu v aplikaci Visual Studio, a zobrazí se výzva k výběru složky pro uložení.</span><span class="sxs-lookup"><span data-stu-id="c4e04-110">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="c4e04-111">V tomto příkladu se název složky zobrazí v <xref:System.Windows.Forms.TextBox> ovládacím prvku ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c4e04-111">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="c4e04-112">Je vhodné umístit umístění do upravitelné oblasti, jako je například <xref:System.Windows.Forms.TextBox> ovládací prvek, aby si uživatelé mohli upravit svůj výběr v případě chyby nebo jiných problémů.</span><span class="sxs-lookup"><span data-stu-id="c4e04-112">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="c4e04-113">Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponentou a <xref:System.Windows.Forms.TextBox> ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="c4e04-113">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="c4e04-114">Chcete-li použít tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastností, která je součástí <xref:System.Security.Permissions.FileIOPermissionAccess> výčtu.</span><span class="sxs-lookup"><span data-stu-id="c4e04-114">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="c4e04-115">Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c4e04-115">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="c4e04-116">Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c4e04-116">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="c4e04-117">Informace o tom, jak ukládat soubory, najdete v tématu [Postupy: ukládání souborů pomocí součásti SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).</span><span class="sxs-lookup"><span data-stu-id="c4e04-117">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c4e04-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4e04-118">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="c4e04-119">FolderBrowserDialog – přehled komponenty (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c4e04-119">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="c4e04-120">Komponenta FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="c4e04-120">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
