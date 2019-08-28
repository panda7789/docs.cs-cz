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
ms.openlocfilehash: c5d88e4942d96ee12e8b9f40156090c874386668
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046256"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Postupy: Ukládání souborů pomocí ovládacího prvku Windows Forms RichTextBox

Ovládací prvek <xref:System.Windows.Forms.RichTextBox> model Windows Forms může zapisovat informace, které se zobrazí v jednom z několika formátů:

- Prostý text

- Prostý text v kódování Unicode

- Rich Text Format (RTF)

- RTF s mezerami místo objektů OLE

- Prostý text s textovou reprezentací objektů OLE

Chcete-li uložit soubor, zavolejte <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodu. Pomocí metody **SaveFile** můžete také ukládat data do datového proudu. Další informace naleznete v tématu <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Uložení obsahu ovládacího prvku do souboru

1. Určete cestu k souboru, který se má uložit.

    K tomu v reálné aplikaci byste obvykle použili <xref:System.Windows.Forms.SaveFileDialog> komponentu. Přehled naleznete v tématu [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).

2. <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> Zavolejte metodu <xref:System.Windows.Forms.RichTextBox> ovládacího prvku, určete soubor, který se má uložit, a volitelně také typ souboru. Pokud voláte metodu s názvem souboru jako s jediným argumentem, soubor bude uložen jako RTF. Chcete-li zadat jiný typ souboru, zavolejte metodu s hodnotou <xref:System.Windows.Forms.RichTextBoxStreamType> výčtu jako svůj druhý argument.

    V následujícím příkladu je cesta nastavená pro umístění souboru s bohatou čárkou ve složce **dokumenty** . Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tuto složku. Zvolíte-li toto umístění, mohou uživatelé s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá, že formulář s <xref:System.Windows.Forms.RichTextBox> ovládacím prvkem již byl přidán.

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
    > Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, musí tato aplikace pro složku vytvořit přístup. Oprávnění se nastavují pomocí seznamů řízení přístupu. Pokud soubor už existuje, aplikace potřebuje jenom přístup pro zápis, což je menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a místo toho udělit přístup ke složce jenom přístup pro čtení jenom pro jeden soubor. Je také bezpečnější zapsat data do složek uživatele než do kořenové složky nebo do složky Program Files.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [Ovládací prvek RichTextBox](richtextbox-control-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
