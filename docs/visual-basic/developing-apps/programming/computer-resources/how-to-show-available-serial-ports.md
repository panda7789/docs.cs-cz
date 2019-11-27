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
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="03f18-102">Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03f18-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="03f18-103">Toto téma popisuje, jak použít `My.Computer.Ports` k zobrazení dostupných sériových portů počítače v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03f18-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="03f18-104">Pokud chcete uživateli dovolit vybrat, který port se má použít, názvy sériových portů se umístí do ovládacího prvku <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="03f18-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03f18-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="03f18-105">Example</span></span>  

 <span data-ttu-id="03f18-106">Tento příklad projde všemi řetězci, které vrací vlastnost `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="03f18-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="03f18-107">Tyto řetězce jsou názvy dostupných sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="03f18-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="03f18-108">Obvykle uživatel vybere, který sériový port by měla aplikace používat ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="03f18-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="03f18-109">V tomto příkladu jsou názvy sériových portů uloženy v ovládacím prvku <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="03f18-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="03f18-110">Další informace naleznete v tématu [ovládací prvek ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="03f18-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="03f18-111">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="03f18-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="03f18-112">Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="03f18-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="03f18-113">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="03f18-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="03f18-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="03f18-114">Compiling the Code</span></span>  

 <span data-ttu-id="03f18-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="03f18-115">This example requires:</span></span>  
  
- <span data-ttu-id="03f18-116">Odkaz na projekt System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="03f18-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="03f18-117">Přístup k členům oboru názvů <xref:System.Windows.Forms>.</span><span class="sxs-lookup"><span data-stu-id="03f18-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="03f18-118">Pokud plně nekvalifikujete názvy členů v kódu, přidejte `Imports` příkaz.</span><span class="sxs-lookup"><span data-stu-id="03f18-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="03f18-119">Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="03f18-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="03f18-120">Má-li formulář <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="03f18-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="03f18-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="03f18-121">Robust Programming</span></span>  

 <span data-ttu-id="03f18-122">K zobrazení dostupných názvů sériového portu není nutné používat ovládací prvek <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="03f18-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="03f18-123">Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="03f18-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="03f18-124">Pokud aplikace nepotřebuje odpověď od uživatele, můžete k zobrazení informací použít ovládací prvek <xref:System.Windows.Forms.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="03f18-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03f18-125">Názvy portů vrácené `My.Computer.Ports.SerialPortNames` můžou být při spuštění ve Windows 98 nesprávné.</span><span class="sxs-lookup"><span data-stu-id="03f18-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="03f18-126">Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, jako je například příkaz `Try...Catch...Finally` nebo příkaz `Using` při použití názvů portů k otevření portů.</span><span class="sxs-lookup"><span data-stu-id="03f18-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f18-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03f18-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="03f18-128">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="03f18-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="03f18-129">Postupy: Posílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="03f18-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="03f18-130">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="03f18-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
