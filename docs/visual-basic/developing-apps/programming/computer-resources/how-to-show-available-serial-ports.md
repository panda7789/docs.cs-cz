---
title: 'Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834644"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="0d5d4-102">Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d5d4-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="0d5d4-103">Toto téma popisuje způsob použití `My.Computer.Ports` k zobrazení dostupných sériových portů v počítači v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="0d5d4-104">Umožňuje uživateli vybrat port, který chcete použít názvy sériových portů jsou umístěny v <xref:System.Windows.Forms.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d5d4-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d5d4-105">Example</span></span>  
 <span data-ttu-id="0d5d4-106">V tomto příkladu cyklickému všechny řetězce, který `My.Computer.Ports.SerialPortNames` vrátí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="0d5d4-107">Tyto řetězce jsou názvy dostupných sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="0d5d4-108">Obvykle uživatel vybere ze seznamu dostupných portů který sériový port aplikace musí používat.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="0d5d4-109">V tomto příkladu jsou názvy sériových portů. uložené v <xref:System.Windows.Forms.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="0d5d4-110">Další informace najdete v tématu [ListBox – ovládací prvek](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0d5d4-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="0d5d4-111">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="0d5d4-112">V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="0d5d4-113">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="0d5d4-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d5d4-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0d5d4-114">Compiling the Code</span></span>  
 <span data-ttu-id="0d5d4-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0d5d4-115">This example requires:</span></span>  
  
-   <span data-ttu-id="0d5d4-116">Odkaz na System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="0d5d4-117">Přístup k členům <xref:System.Windows.Forms> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="0d5d4-118">Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="0d5d4-119">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="0d5d4-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="0d5d4-120">Obsahující formulář <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0d5d4-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="0d5d4-121">Robust Programming</span></span>  
 <span data-ttu-id="0d5d4-122">Není nutné používat <xref:System.Windows.Forms.ListBox> ovládací prvek pro zobrazení názvy dostupných sériových portů.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="0d5d4-123">Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="0d5d4-124">Pokud aplikace nepotřebuje odpověď od uživatele, můžete použít <xref:System.Windows.Forms.TextBox> ovládací prvek pro zobrazení informací.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d5d4-125">Názvy port vrácené `My.Computer.Ports.SerialPortNames` může být nesprávné při spuštění na Windows 98.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="0d5d4-126">Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, například `Try...Catch...Finally` příkazu nebo `Using` prohlášení, při použití názvu port otevřít porty.</span><span class="sxs-lookup"><span data-stu-id="0d5d4-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d5d4-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d5d4-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="0d5d4-128">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="0d5d4-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="0d5d4-129">Postupy: Odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="0d5d4-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="0d5d4-130">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="0d5d4-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
