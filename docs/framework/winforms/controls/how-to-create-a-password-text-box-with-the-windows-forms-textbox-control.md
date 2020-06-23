---
title: Textové pole pro vytvoření hesla pomocí ovládacího prvku TextBox
description: Naučte se, jak model Windows Forms vytvoří text, který zobrazuje zástupné znaky, když uživatel zadá řetězec.
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
ms.openlocfilehash: 6d7e61eefa44ce3152aa77e3922bde471a4aeaf3
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904309"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a><span data-ttu-id="df5f8-103">Postupy: Vytvoření textového pole hesla pomocí ovládacího prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="df5f8-103">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>

<span data-ttu-id="df5f8-104">Pole pro heslo je model Windows Forms textové pole, které zobrazuje zástupné znaky, když uživatel zadá řetězec.</span><span class="sxs-lookup"><span data-stu-id="df5f8-104">A password box is a Windows Forms text box that displays placeholder characters while a user types a string.</span></span>

### <a name="to-create-a-password-text-box"></a><span data-ttu-id="df5f8-105">Vytvoření textového pole pro heslo</span><span class="sxs-lookup"><span data-stu-id="df5f8-105">To create a password text box</span></span>

1. <span data-ttu-id="df5f8-106">Nastavte <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na konkrétní znak.</span><span class="sxs-lookup"><span data-stu-id="df5f8-106">Set the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property of the <xref:System.Windows.Forms.TextBox> control to a specific character.</span></span>

    <span data-ttu-id="df5f8-107"><xref:System.Windows.Forms.TextBox.PasswordChar%2A>Vlastnost určuje znak zobrazený v textovém poli.</span><span class="sxs-lookup"><span data-stu-id="df5f8-107">The <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property specifies the character displayed in the text box.</span></span> <span data-ttu-id="df5f8-108">Například pokud chcete, aby se v poli heslo zobrazovaly hvězdičky, zadejte \* pro <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnost v okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df5f8-108">For example, if you want asterisks displayed in the password box, specify \* for the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property in the Properties window.</span></span> <span data-ttu-id="df5f8-109">Bez ohledu na to, jaký znak má uživatel v textovém poli, se zobrazí hvězdička.</span><span class="sxs-lookup"><span data-stu-id="df5f8-109">Then, regardless of what character a user types in the text box, an asterisk is displayed.</span></span>

2. <span data-ttu-id="df5f8-110">Volitelné Nastavte <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df5f8-110">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A> property.</span></span> <span data-ttu-id="df5f8-111">Vlastnost určuje, kolik znaků lze zadat do textového pole.</span><span class="sxs-lookup"><span data-stu-id="df5f8-111">The property determines how many characters can be typed in the text box.</span></span> <span data-ttu-id="df5f8-112">Pokud je překročena maximální délka, systém vygeneruje zvukový signál a textové pole nepřijímá žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="df5f8-112">If the maximum length is exceeded, the system emits a beep and the text box does not accept any more characters.</span></span> <span data-ttu-id="df5f8-113">Mějte na paměti, že to nebudete chtít udělat, protože maximální délka hesla může být použita pro hackery, kteří se pokoušejí uhodnout heslo.</span><span class="sxs-lookup"><span data-stu-id="df5f8-113">Note that you may not wish to do this as the maximum length of a password may be of use to hackers who are trying to guess the password.</span></span>

    <span data-ttu-id="df5f8-114">Následující příklad kódu ukazuje, jak inicializovat textové pole, které bude akceptovat řetězec o délce až 14 znaků a zobrazit hvězdičky namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="df5f8-114">The following code example shows how to initialize a text box that will accept a string up to 14 characters long and display asterisks in place of the string.</span></span> <span data-ttu-id="df5f8-115">`InitializeMyControl`Procedura se neprovede automaticky, musí být volána.</span><span class="sxs-lookup"><span data-stu-id="df5f8-115">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="df5f8-116">Použití <xref:System.Windows.Forms.TextBox.PasswordChar%2A> vlastnosti v textovém poli vám může pomoci zajistit, že jiní uživatelé nebudou moci určit heslo uživatele, pokud budou sledovat uživatele.</span><span class="sxs-lookup"><span data-stu-id="df5f8-116">Using the <xref:System.Windows.Forms.TextBox.PasswordChar%2A> property on a text box can help ensure that other people will not be able to determine a user's password if they observe the user entering it.</span></span> <span data-ttu-id="df5f8-117">Tato míra zabezpečení nepokrývá žádné řazení úložiště ani přenos hesla, ke kterým může dojít z důvodu vaší logiky aplikace.</span><span class="sxs-lookup"><span data-stu-id="df5f8-117">This security measure does not cover any sort of storage or transmission of the password that can occur due to your application logic.</span></span> <span data-ttu-id="df5f8-118">Vzhledem k tomu, že zadaný text není jakýmkoli způsobem zašifrovaný, měli byste s ním zacházet stejně jako s jinými důvěrnými údaji.</span><span class="sxs-lookup"><span data-stu-id="df5f8-118">Because the text entered is not encrypted in any way, you should treat it as you would any other confidential data.</span></span> <span data-ttu-id="df5f8-119">I když se nezobrazuje jako takový, heslo se pořád považuje za řetězec s prostým textem (Pokud jste neimplementovali nějaké další bezpečnostní opatření).</span><span class="sxs-lookup"><span data-stu-id="df5f8-119">Even though it does not appear as such, the password is still being treated as a plain-text string (unless you have implemented some additional security measure).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="df5f8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="df5f8-120">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="df5f8-121">Přehled ovládacího prvku TextBox</span><span class="sxs-lookup"><span data-stu-id="df5f8-121">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="df5f8-122">Postupy: Řízení místa vložení v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="df5f8-122">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="df5f8-123">Postupy: Vytvoření textového pole určeného jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df5f8-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="df5f8-124">Postupy: Vkládání uvozovek do řetězce</span><span class="sxs-lookup"><span data-stu-id="df5f8-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="df5f8-125">Postupy: Výběr textu v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="df5f8-125">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="df5f8-126">Postupy: Zobrazování více řádků v ovládacím prvku Windows Forms TextBox</span><span class="sxs-lookup"><span data-stu-id="df5f8-126">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="df5f8-127">TextBox – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="df5f8-127">TextBox Control</span></span>](textbox-control-windows-forms.md)
