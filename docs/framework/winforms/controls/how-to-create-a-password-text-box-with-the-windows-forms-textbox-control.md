---
title: 'Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: ab5df1233c16a7ce076efa817fb14808b588ebcd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300980"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox
Pole pro heslo je textové pole formulářů Windows, která zobrazuje zástupné znaky, když uživatel zadá řetězec.  
  
### <a name="to-create-a-password-text-box"></a>K vytvoření textového pole hesla  
  
1. Nastavte <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na konkrétní znak.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Vlastnost určuje znak, který zobrazí v textovém poli. Například pokud chcete hvězdičky z obou stran zobrazí v poli hesla, zadejte * pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastností v okně Vlastnosti. Bez ohledu na to, jakou znakovou uživatel zadá do textového pole, pak se zobrazí hvězdičku.  
  
2. (Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> vlastnost. Vlastnost určuje, kolik znaků lze zadat do textového pole. Pokud je překročen maximální počet znaků, systém vydá zvukový signál a do textového pole nepřijímá žádné další znaky. Všimněte si, že pravděpodobně chcete to udělat jako maximální délku hesla může být použita hackery, kteří se snaží uhodnout heslo.  
  
     Následující příklad kódu ukazuje, jak inicializovat textové pole, která bude přijímat řetězec až 14 znaků dlouhé a zobrazení hvězdičky z obou stran namísto řetězce. `InitializeMyControl` Postup nespustí automaticky, musí být volána.  
  
    > [!IMPORTANT]
    >  Použití <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v textovém poli můžete zajistit, že ostatní uživatelé nebudou moct určit heslo uživatele, pokud sledují uživatele při jeho zadávání. Tato bezpečnostní opatření nepopisuje jakýkoli druh úložiště nebo přenosu heslo, které může dojít z vaší aplikace logiky. Vzhledem k tomu, že zadaný text není zašifrovaný žádným způsobem, by měly zpracovávat stejně jako jakákoli důvěrná data. I když není zobrazen jako takové, hesla je stále se zachází jako řetězec ve formátu prostého textu (Pokud jste implementovali některé další bezpečnostní opatření).  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TextBox>
- [Přehled ovládacího prvku TextBox](textbox-control-overview-windows-forms.md)
- [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Postupy: Vytvoření textového pole určeného jen pro čtení](how-to-create-a-read-only-text-box-windows-forms.md)
- [Postupy: Vkládání uvozovek do řetězce](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [Ovládací prvek TextBox](textbox-control-windows-forms.md)
