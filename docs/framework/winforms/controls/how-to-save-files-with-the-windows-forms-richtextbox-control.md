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
ms.openlocfilehash: d28aeaefca6f8aa13607f1c1e6f72557ef536754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> řízení může zapsat informace se zobrazí v některém z formátů:  
  
-   Prostý text  
  
-   Prostý text v kódu Unicode  
  
-   RTF (Rich Text Format)  
  
-   RTF prostory místo OLE – objekty  
  
-   Ve formátu prostého textu s textovou reprezentaci OLE – objekty  
  
 Chcete-li uložit soubor, volejte <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metoda. Můžete také **SaveFile** metoda k uložení dat do datového proudu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Chcete uložit obsah ovládacího prvku do souboru  
  
1.  Určete cestu k souboru uložit.  
  
     K tomu v reálné aplikaci byste obvykle použili <xref:System.Windows.Forms.SaveFileDialog> součásti. Přehled najdete v tématu [SaveFileDialog – přehled komponenty](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).  
  
2.  Volání <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> řízení, soubor uložte a volitelně typu souboru. Pokud jste volali metodu s názvem souboru jako argument pouze, uloží soubor ve formátu RTF. Chcete-li určit jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako druhý argument.  
  
     V následujícím příkladu cesta pro umístění souboru formátovaného textu je nastavena **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky. Výběr toto umístění také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládací prvek již přidán.  
  
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
    >  Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace potřebuje k vytvoření souboru, tuto aplikaci potřebuje vytvořit přístup ke složce. Jsou oprávnění nastavena pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze k zápisu, a menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a jenom udělit přístup pro čtení do jednoho souboru, než vytvořit přístupu pro složku. Navíc je bezpečnější zapsat data do složek uživatele než do kořenové složky nebo ve složce Program Files.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox – ovládací prvek](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
