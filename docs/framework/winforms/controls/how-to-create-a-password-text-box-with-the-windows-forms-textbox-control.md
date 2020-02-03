---
title: Textové pole pro vytvoření hesla pomocí ovládacího prvku TextBox
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
ms.openlocfilehash: ff4706a736d15f14cf437c808219e9088773dc6d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731282"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="0fd69-102">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-102">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="0fd69-103">Pole pro heslo je model Windows Forms textové pole, které zobrazuje zástupné znaky, když uživatel zadá řetězec.</span><span class="sxs-lookup"><span data-stu-id="0fd69-103">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="0fd69-104">Vytvoření textového pole pro heslo</span><span class="sxs-lookup"><span data-stu-id="0fd69-104">To create a password text box</span></span>

1. <span data-ttu-id="0fd69-105">Nastavte vlastnost <xref:System.Windows.Forms.TextBox.PasswordChar%2A> ovládacího prvku <xref:System.Windows.Forms.TextBox> na konkrétní znak.</span><span class="sxs-lookup"><span data-stu-id="0fd69-105">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="0fd69-106">Vlastnost <xref:System.Windows.Forms.TextBox.PasswordChar%2A> určuje znak zobrazený v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="0fd69-106">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="0fd69-107">Například pokud chcete, aby se v poli heslo zobrazovaly hvězdičky, zadejte pro vlastnost <xref:System.Windows.Forms.TextBox.PasswordChar%2A> v okno Vlastnosti hodnotu \*.</span><span class="sxs-lookup"><span data-stu-id="0fd69-107">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="0fd69-108">Bez ohledu na to, jaký znak má uživatel v textovém poli, se zobrazí hvězdička.</span><span class="sxs-lookup"><span data-stu-id="0fd69-108">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="0fd69-109">Volitelné Nastavte vlastnost <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fd69-109">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="0fd69-110">Vlastnost určuje, kolik znaků lze zadat do textového pole.</span><span class="sxs-lookup"><span data-stu-id="0fd69-110">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="0fd69-111">Pokud je překročena maximální délka, systém vygeneruje zvukový signál a textové pole nepřijímá žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="0fd69-111">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="0fd69-112">Mějte na paměti, že to nebudete chtít udělat, protože maximální délka hesla může být použita pro hackery, kteří se pokoušejí uhodnout heslo.</span><span class="sxs-lookup"><span data-stu-id="0fd69-112">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="0fd69-113">Následující příklad kódu ukazuje, jak inicializovat textové pole, které bude akceptovat řetězec o délce až 14 znaků a zobrazit hvězdičky namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="0fd69-113">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="0fd69-114">Postup `InitializeMyControl` nebude proveden automaticky; musí být volána.</span><span class="sxs-lookup"><span data-stu-id="0fd69-114">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0fd69-115">Použití vlastnosti <xref:System.Windows.Forms.TextBox.PasswordChar%2A> v textovém poli vám může pomoci zajistit, že jiní uživatelé nebudou moci určit heslo uživatele, pokud budou sledovat uživatele, který ho zadává.</span><span class="sxs-lookup"><span data-stu-id="0fd69-115">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="0fd69-116">Tato míra zabezpečení nepokrývá žádné řazení úložiště ani přenos hesla, ke kterým může dojít z důvodu vaší logiky aplikace.</span><span class="sxs-lookup"><span data-stu-id="0fd69-116">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="0fd69-117">Vzhledem k tomu, že zadaný text není jakýmkoli způsobem zašifrovaný, měli byste s ním zacházet stejně jako s jinými důvěrnými údaji.</span><span class="sxs-lookup"><span data-stu-id="0fd69-117">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="0fd69-118">I když se nezobrazuje jako takový, heslo se pořád považuje za řetězec s prostým textem (Pokud jste neimplementovali nějaké další bezpečnostní opatření).</span><span class="sxs-lookup"><span data-stu-id="0fd69-118">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0fd69-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fd69-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="0fd69-120">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="0fd69-121">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="0fd69-122">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0fd69-122">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="0fd69-123">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="0fd69-123">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="0fd69-124">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-124">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0fd69-125">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="0fd69-126">Ovládací prvek TextBox</span><span class="sxs-lookup"><span data-stu-id="0fd69-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
