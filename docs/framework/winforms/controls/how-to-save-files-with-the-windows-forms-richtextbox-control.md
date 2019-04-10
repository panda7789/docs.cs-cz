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
ms.openlocfilehash: 4784ddd563ccec0f7e6271700781ee1b5d3ac105
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318413"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox
Windows Forms <xref:System.Windows.Forms.RichTextBox> ovládací prvek lze zapsat informace se zobrazí v jednom z několika formátů:  
  
-   Prostý text  
  
-   Kódování Unicode ve formátu prostého textu  
  
-   Rich-Text Format (RTF)  
  
-   RTF prostory místo objekty OLE  
  
-   Prostý text s textovou reprezentaci řetězce objekty OLE  
  
 Chcete-li uložit soubor, zavolejte <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody. Můžete také použít **SaveFile** metoda k ukládání dat do datového proudu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Chcete uložit obsah ovládacího prvku do souboru  
  
1. Určete cestu k souboru, který se má uložit.  
  
     K tomu v reálné aplikaci byste obvykle použili <xref:System.Windows.Forms.SaveFileDialog> komponenty. Přehled najdete v tématu [SaveFileDialog – přehled komponenty](savefiledialog-component-overview-windows-forms.md).  
  
2. Volání <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodu <xref:System.Windows.Forms.RichTextBox> ovládací prvek, pro uložení souboru a volitelně typu souboru. Pokud jste volali metodu s názvem souboru jako její jediný argument, soubor se uloží ve formátu RTF. Chcete-li zadat jiný typ souboru, volejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčet jako druhý argument.  
  
     V následujícím příkladu nastavena cesta pro umístění souboru formátovaného textu je **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat této složky. Výběrem tohoto umístění také umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spusťte aplikaci. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.RichTextBox> ovládací prvek již přidán.  
  
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
    >  Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace potřebuje k vytvoření souboru, aplikace potřebuje vytvořit přístup ke složce. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace potřebuje pouze přístup pro zápis, a menší oprávnění. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a jenom udělit přístup pro čtení do jednoho souboru, ne vytvořit přístup ke složce. Navíc je bezpečnější zapsat data do uživatelské složky než do kořenové složky nebo ve složce Program Files.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
