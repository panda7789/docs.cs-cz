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
ms.openlocfilehash: 2bff105d5c97a8b98d094a1ce3a4f033aa5971be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116074"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Postupy: Výběr složek pomocí komponenty Windows Forms FolderBrowserDialog
Často v rámci aplikace Windows, které vytvoříte, budete muset vyzvat uživatele, vyberte složku, většina často budou sadu souborů. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> komponenta umožňuje snadno provést tuto úlohu.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Chcete-li zvolit složky s FolderBrowserDialog – komponenta  
  
1.  V postupu, zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> komponenty <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnosti naleznete v tématu Jak bylo ukončeno dialogových oken a získání hodnoty <xref:System.Windows.Forms.FolderBrowserDialog> komponenty <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost.  
  
2.  Pokud je nutné do složky sady úplně nahoře, který se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která přebírá členem <xref:System.Environment.SpecialFolder> výčtu.  
  
3.  Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnost, která určuje, textový řetězec, který se zobrazí v horní části stromu zobrazení prohlížeč složek.  
  
     V následujícím příkladu <xref:System.Windows.Forms.FolderBrowserDialog> komponenty slouží k výběru složky, podobně jako při vytvoření projektu v sadě Visual Studio a vyzváni k výběru pro uložte ho do složky. V tomto příkladu název složky se následně zobrazí <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři. Je vhodné umístit umístění upravitelné oblasti, jako například <xref:System.Windows.Forms.TextBox> řídit, takže uživatelé mohou upravovat jejich výběr v případě chyby nebo jiné problémy. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> komponenty a <xref:System.Windows.Forms.TextBox> ovládacího prvku.  
  
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
    >  Pro tuto třídu použít, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastnost, která je součástí sady <xref:System.Security.Permissions.FileIOPermissionAccess> výčtu. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, procesu může vyvolat výjimku z důvodu dostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../misc/code-access-security-basics.md).  
  
 Informace o tom, jak uložit soubory, naleznete v tématu [jak: Ukládání souborů pomocí součásti SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog – přehled komponenty (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [Komponenta FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
