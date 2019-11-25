---
title: 'Postupy: Zobrazení dostupných sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345578"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="ada0b-102">Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ada0b-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="ada0b-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ada0b-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="ada0b-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span><span class="sxs-lookup"><span data-stu-id="ada0b-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ada0b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ada0b-105">Example</span></span>  

 <span data-ttu-id="ada0b-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span><span class="sxs-lookup"><span data-stu-id="ada0b-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="ada0b-107">These strings are the names of the available serial ports on the computer.</span><span class="sxs-lookup"><span data-stu-id="ada0b-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="ada0b-108">Typically, a user selects which serial port the application should use from the list of available ports.</span><span class="sxs-lookup"><span data-stu-id="ada0b-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="ada0b-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span><span class="sxs-lookup"><span data-stu-id="ada0b-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="ada0b-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ada0b-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="ada0b-111">This code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="ada0b-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ada0b-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span><span class="sxs-lookup"><span data-stu-id="ada0b-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="ada0b-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ada0b-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ada0b-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ada0b-114">Compiling the Code</span></span>  

 <span data-ttu-id="ada0b-115">This example requires:</span><span class="sxs-lookup"><span data-stu-id="ada0b-115">This example requires:</span></span>  
  
- <span data-ttu-id="ada0b-116">A project reference to System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="ada0b-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="ada0b-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span><span class="sxs-lookup"><span data-stu-id="ada0b-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="ada0b-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span><span class="sxs-lookup"><span data-stu-id="ada0b-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="ada0b-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="ada0b-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="ada0b-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="ada0b-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ada0b-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ada0b-121">Robust Programming</span></span>  

 <span data-ttu-id="ada0b-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span><span class="sxs-lookup"><span data-stu-id="ada0b-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="ada0b-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span><span class="sxs-lookup"><span data-stu-id="ada0b-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="ada0b-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span><span class="sxs-lookup"><span data-stu-id="ada0b-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ada0b-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span><span class="sxs-lookup"><span data-stu-id="ada0b-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="ada0b-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span><span class="sxs-lookup"><span data-stu-id="ada0b-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada0b-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ada0b-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="ada0b-128">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="ada0b-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="ada0b-129">Postupy: Posílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="ada0b-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="ada0b-130">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="ada0b-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
