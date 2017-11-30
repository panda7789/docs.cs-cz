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
ms.openlocfilehash: 0824fb70fa67628326af38ff7fb5e6c097a0378c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Postupy: Výběr složek se součástí Windows Forms FolderBrowserDialog
V rámci aplikace systému Windows, které vytvoříte, často, bude mít vyzve uživatele, vyberte složku, většina často k uložení sady souborů. Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> součást umožňuje snadno dosáhnout.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Chcete-li zvolit složky s FolderBrowserDialog – komponenta  
  
1.  V postupu, zkontrolujte <xref:System.Windows.Forms.FolderBrowserDialog> součásti <xref:System.Windows.Forms.Form.DialogResult%2A> vlastnosti chcete zobrazit, jak bylo ukončeno dialogové okno a získat hodnotu <xref:System.Windows.Forms.FolderBrowserDialog> součásti <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> vlastnost.  
  
2.  Pokud budete potřebovat sadu nejvyšší úrovni složky, která se zobrazí ve stromovém zobrazení dialogového okna, nastavte <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> vlastnost, která přebírá členem <xref:System.Environment.SpecialFolder> výčtu.  
  
3.  Kromě toho můžete nastavit <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> vlastnosti, která určuje také textový řetězec, který se zobrazí v horní části stromovém zobrazení složky prohlížeče.  
  
     V následujícím příkladu <xref:System.Windows.Forms.FolderBrowserDialog> součást slouží k výběru složky, podobně jako při vytvoření projektu v sadě Visual Studio a vyzváni k výběru složku pro uložení v. V tomto příkladu se následně zobrazí název složky v <xref:System.Windows.Forms.TextBox> ovládací prvek na formuláři. Je vhodné umístit umístění upravitelné oblast, například <xref:System.Windows.Forms.TextBox> řídit, tak, aby uživatelé mohou upravovat jejich výběr v případě chyby nebo jiných problémů. Tento příklad předpokládá formulář s <xref:System.Windows.Forms.FolderBrowserDialog> součásti a <xref:System.Windows.Forms.TextBox> ovládacího prvku.  
  
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
    >  Pokud chcete používat tuto třídu, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> vlastnost, která je součástí z <xref:System.Security.Permissions.FileIOPermissionAccess> – výčet. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, proces může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Informace o tom, jak ukládat soubory najdete v tématu [postupy: ukládání souborů pomocí součásti SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [FolderBrowserDialog – přehled komponenty (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog – komponenta](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
