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
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="94834-102">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="94834-103">Pole pro heslo je Windows Forms textové pole, které zobrazí zástupné znaky, když uživatel zadá řetězec.</span><span class="sxs-lookup"><span data-stu-id="94834-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="94834-104">K vytvoření textového pole hesla</span><span class="sxs-lookup"><span data-stu-id="94834-104">To create a password text box</span></span>  
  
1.  <span data-ttu-id="94834-105">Nastavte <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost <xref:System.Windows.Forms.TextBox> řízení zvláštní znak.</span><span class="sxs-lookup"><span data-stu-id="94834-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="94834-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Vlastnost určuje znak zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="94834-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="94834-107">Například pokud chcete hvězdičky zobrazí do pole heslo, zadejte * pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="94834-107">For example, if you want asterisks displayed in the password box, specify * for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="94834-108">Bez ohledu na to, jaké znak uživatel zadá do textového pole, pak se zobrazí hvězdičku.</span><span class="sxs-lookup"><span data-stu-id="94834-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2.  <span data-ttu-id="94834-109">(Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="94834-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="94834-110">Vlastnost určuje, kolik znaků lze zadat do textového pole.</span><span class="sxs-lookup"><span data-stu-id="94834-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="94834-111">Pokud dojde k překročení maximální délku, systém vysílá zvukový signál a textového pole nepřijímá žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="94834-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="94834-112">Všimněte si, že pravděpodobně chcete jako maximální délku hesla k tomu může být použita hackery, kteří se snaží uhodnout heslo.</span><span class="sxs-lookup"><span data-stu-id="94834-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="94834-113">Následující příklad kódu ukazuje, jak k chybě při inicializaci textové pole, které budou přijímat řetězec až 14 znaků a zobrazení hvězdičky místo řetězec.</span><span class="sxs-lookup"><span data-stu-id="94834-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="94834-114">`InitializeMyControl` Postup nebude automaticky spustit; musí být volána.</span><span class="sxs-lookup"><span data-stu-id="94834-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="94834-115">Pomocí <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v textovém poli může pomoci zajistit, že ostatní uživatelé nebudou moci určit heslo uživatele, pokud sledují uživatele při jeho zadávání.</span><span class="sxs-lookup"><span data-stu-id="94834-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="94834-116">Tato bezpečnostní opatření nepopisuje všechny řazení úložiště nebo přenos heslo, které můžou nastat v důsledku logiky aplikace.</span><span class="sxs-lookup"><span data-stu-id="94834-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="94834-117">Vzhledem k tomu, že zadaný text není zašifrovaná žádným způsobem, by měly zpracovávat stejně jako jiné důvěrné údaje.</span><span class="sxs-lookup"><span data-stu-id="94834-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="94834-118">I když se nezobrazí jako takový, heslo bude stále zacházeno jako řetězec ve formátu prostého textu (Pokud jste implementovali některé další bezpečnostní opatření).</span><span class="sxs-lookup"><span data-stu-id="94834-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94834-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="94834-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="94834-120">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="94834-121">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="94834-122">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94834-122">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="94834-123">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="94834-123">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="94834-124">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="94834-125">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="94834-126">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="94834-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
