---
title: "Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox"
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
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fe8c3c6ac3c0f47f5e78aa7ff3242a0c69c7f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox
Pole pro heslo je Windows Forms textové pole, které zobrazí zástupné znaky, když uživatel zadá řetězec.  
  
### <a name="to-create-a-password-text-box"></a>K vytvoření textového pole hesla  
  
1.  Nastavte <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost <xref:System.Windows.Forms.TextBox> řízení zvláštní znak.  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A> Vlastnost určuje znak zobrazí v textovém poli. Například pokud chcete hvězdičky zobrazí do pole heslo, zadejte * pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v okně Vlastnosti. Bez ohledu na to, jaké znak uživatel zadá do textového pole, pak se zobrazí hvězdičku.  
  
2.  (Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> vlastnost. Vlastnost určuje, kolik znaků lze zadat do textového pole. Pokud dojde k překročení maximální délku, systém vysílá zvukový signál a textového pole nepřijímá žádné další znaky. Všimněte si, že pravděpodobně chcete jako maximální délku hesla k tomu může být použita hackery, kteří se snaží uhodnout heslo.  
  
     Následující příklad kódu ukazuje, jak k chybě při inicializaci textové pole, které budou přijímat řetězec až 14 znaků a zobrazení hvězdičky místo řetězec. `InitializeMyControl` Postup nebude automaticky spustit; musí být volána.  
  
    > [!IMPORTANT]
    >  Pomocí <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v textovém poli může pomoci zajistit, že ostatní uživatelé nebudou moci určit heslo uživatele, pokud sledují uživatele při jeho zadávání. Tato bezpečnostní opatření nepopisuje všechny řazení úložiště nebo přenos heslo, které můžou nastat v důsledku logiky aplikace. Vzhledem k tomu, že zadaný text není zašifrovaná žádným způsobem, by měly zpracovávat stejně jako jiné důvěrné údaje. I když se nezobrazí jako takový, heslo bude stále zacházeno jako řetězec ve formátu prostého textu (Pokud jste implementovali některé další bezpečnostní opatření).  
  
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
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TextBox>  
 [Přehled ovládacího prvku TextBox](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Postupy: Vytvoření textového pole určeného jen pro čtení](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Postupy: Vkládání uvozovek do řetězce](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [Ovládací prvek TextBox](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
