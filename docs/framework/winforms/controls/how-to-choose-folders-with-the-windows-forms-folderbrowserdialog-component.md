---
title: Výběr složek s komponentou FolderBrowserDialog
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
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742225"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog

V rámci aplikací systému Windows, které vytvoříte, budete často muset vyzvat uživatele k výběru složky, nejčastěji k uložení sady souborů. Součást model Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> vám umožní snadnou tuto úlohu provést.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Výběr složek pomocí komponenty FolderBrowserDialog

1. V proceduře Zkontrolujte vlastnost <xref:System.Windows.Forms.Form.DialogResult%2A> <xref:System.Windows.Forms.FolderBrowserDialog> Component, abyste viděli, jak se dialogové okno zavřelo, a získat hodnotu vlastnosti <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> <xref:System.Windows.Forms.FolderBrowserDialog> komponenty.

2. Pokud potřebujete nastavit složku nejvyšší úrovně, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, která přijímá člena <xref:System.Environment.SpecialFolder> výčtu.

3. Kromě toho můžete nastavit vlastnost <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>, která určuje textový řetězec, který se zobrazí v horní části stromového zobrazení prohlížeče složky.

    V následujícím příkladu se <xref:System.Windows.Forms.FolderBrowserDialog> komponenta používá k výběru složky, podobně jako při vytváření projektu v aplikaci Visual Studio, a zobrazí se výzva k výběru složky pro uložení. V tomto příkladu se název složky zobrazí v ovládacím prvku <xref:System.Windows.Forms.TextBox> ve formuláři. Je vhodné umístit umístění do upravitelné oblasti, například <xref:System.Windows.Forms.TextBox> ovládacího prvku, aby si uživatelé mohli upravit svůj výběr v případě chyby nebo jiných problémů. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponentou a ovládacím prvkem <xref:System.Windows.Forms.TextBox>.

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
    > Chcete-li použít tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělené vlastností <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>, která je součástí výčtu <xref:System.Security.Permissions.FileIOPermissionAccess>. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../misc/code-access-security-basics.md).

Informace o tom, jak ukládat soubory, najdete v tématu [Postupy: ukládání souborů pomocí součásti SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Přehled komponenty FolderBrowserDialog (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Komponenta FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
