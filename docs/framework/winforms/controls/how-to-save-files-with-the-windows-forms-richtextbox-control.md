---
title: 'Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox'
ms.date: 03/30/2017
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
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 [Ovládací prvek RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
