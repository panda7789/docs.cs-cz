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
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog

V rámci aplikací systému Windows, které vytvoříte, budete často muset vyzvat uživatele k výběru složky, nejčastěji k uložení sady souborů. <xref:System.Windows.Forms.FolderBrowserDialog>Tato součást umožňuje snadnou akci provádět pomocí model Windows Forms komponenty.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Výběr složek pomocí komponenty FolderBrowserDialog

1. V proceduře zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnost komponenty a podívejte se, jak se dialogové okno zavřelo, a získejte hodnotu <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> Vlastnosti komponenty.

2. Pokud potřebujete nastavit složku nejvyšší úrovně, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která převezme člena <xref:System.Environment.SpecialFolder> výčtu.

3. Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnost, která určuje textový řetězec, který se zobrazí v horní části stromového zobrazení prohlížeče složky.

    V následujícím příkladu se <xref:System.Windows.Forms.FolderBrowserDialog> komponenta používá k výběru složky, podobně jako při vytváření projektu v aplikaci Visual Studio, a zobrazí se výzva k výběru složky pro uložení. V tomto příkladu se název složky zobrazí v <xref:System.Windows.Forms.TextBox> ovládacím prvku ve formuláři. Je vhodné umístit umístění do upravitelné oblasti, jako je například <xref:System.Windows.Forms.TextBox> ovládací prvek, aby si uživatelé mohli upravit svůj výběr v případě chyby nebo jiných problémů. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponentou a <xref:System.Windows.Forms.TextBox> ovládacím prvkem.

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
    > Chcete-li použít tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělené <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastností, která je součástí <xref:System.Security.Permissions.FileIOPermissionAccess> výčtu. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

Informace o tom, jak ukládat soubory, najdete v tématu [Postupy: ukládání souborů pomocí součásti SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog – přehled komponenty (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Komponenta FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
