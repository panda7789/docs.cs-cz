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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746751"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="cb503-102">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>
<span data-ttu-id="cb503-103">Pole pro heslo je textové pole formulářů Windows, která zobrazuje zástupné znaky, když uživatel zadá řetězec.</span><span class="sxs-lookup"><span data-stu-id="cb503-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>  
  
### <a name="to-create-a-password-text-box"></a><span data-ttu-id="cb503-104">K vytvoření textového pole hesla</span><span class="sxs-lookup"><span data-stu-id="cb503-104">To create a password text box</span></span>  
  
1. <span data-ttu-id="cb503-105">Nastavte <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na konkrétní znak.</span><span class="sxs-lookup"><span data-stu-id="cb503-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>  
  
     <span data-ttu-id="cb503-106"><xref:System.Windows.Forms.TextBox.PasswordChar%2A> Vlastnost určuje znak, který zobrazí v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="cb503-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="cb503-107">Například pokud chcete hvězdičky z obou stran zobrazí v poli hesla, zadejte \* pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastností v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cb503-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="cb503-108">Bez ohledu na to, jakou znakovou uživatel zadá do textového pole, pak se zobrazí hvězdičku.</span><span class="sxs-lookup"><span data-stu-id="cb503-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>  
  
2. <span data-ttu-id="cb503-109">(Volitelné) Nastavte <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb503-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="cb503-110">Vlastnost určuje, kolik znaků lze zadat do textového pole.</span><span class="sxs-lookup"><span data-stu-id="cb503-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="cb503-111">Pokud je překročen maximální počet znaků, systém vydá zvukový signál a do textového pole nepřijímá žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="cb503-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="cb503-112">Všimněte si, že pravděpodobně chcete to udělat jako maximální délku hesla může být použita hackery, kteří se snaží uhodnout heslo.</span><span class="sxs-lookup"><span data-stu-id="cb503-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>  
  
     <span data-ttu-id="cb503-113">Následující příklad kódu ukazuje, jak inicializovat textové pole, která bude přijímat řetězec až 14 znaků dlouhé a zobrazení hvězdičky z obou stran namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="cb503-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="cb503-114">`InitializeMyControl` Postup nespustí automaticky, musí být volána.</span><span class="sxs-lookup"><span data-stu-id="cb503-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="cb503-115">Použití <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v textovém poli můžete zajistit, že ostatní uživatelé nebudou moct určit heslo uživatele, pokud sledují uživatele při jeho zadávání.</span><span class="sxs-lookup"><span data-stu-id="cb503-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="cb503-116">Tato bezpečnostní opatření nepopisuje jakýkoli druh úložiště nebo přenosu heslo, které může dojít z vaší aplikace logiky.</span><span class="sxs-lookup"><span data-stu-id="cb503-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="cb503-117">Vzhledem k tomu, že zadaný text není zašifrovaný žádným způsobem, by měly zpracovávat stejně jako jakákoli důvěrná data.</span><span class="sxs-lookup"><span data-stu-id="cb503-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="cb503-118">I když není zobrazen jako takové, hesla je stále se zachází jako řetězec ve formátu prostého textu (Pokud jste implementovali některé další bezpečnostní opatření).</span><span class="sxs-lookup"><span data-stu-id="cb503-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb503-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb503-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="cb503-120">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="cb503-121">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb503-122">Postupy: Vytvoření pole jen pro čtení textu</span><span class="sxs-lookup"><span data-stu-id="cb503-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="cb503-123">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="cb503-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="cb503-124">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb503-125">Postupy: Zobrazit více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="cb503-126">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="cb503-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
