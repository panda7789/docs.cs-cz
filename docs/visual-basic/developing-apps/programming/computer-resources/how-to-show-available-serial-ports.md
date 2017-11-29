---
title: "Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1dc12d8ad4c27eff346ccb6a7f5fd2ae3bd76701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="150f2-102">Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="150f2-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="150f2-103">Toto téma popisuje postup použití `My.Computer.Ports` k zobrazení dostupných sériových portů počítače v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="150f2-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="150f2-104">Povolit uživatelům vyberte port, který chcete použít, jsou umístěny názvy sériových portů v <xref:System.Windows.Forms.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="150f2-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="150f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="150f2-105">Example</span></span>  
 <span data-ttu-id="150f2-106">Tento příklad cyklicky prochází přes všechny řetězce, `My.Computer.Ports.SerialPortNames` vrátí vlastnost.</span><span class="sxs-lookup"><span data-stu-id="150f2-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="150f2-107">Tyto řetězce jsou názvy dostupných sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="150f2-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="150f2-108">Obvykle se uživatel vybere ze seznamu dostupných portů sériový port, který by aplikace měla použít.</span><span class="sxs-lookup"><span data-stu-id="150f2-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="150f2-109">V tomto příkladu jsou uložené názvy sériových portů v <xref:System.Windows.Forms.ListBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="150f2-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="150f2-110">Další informace najdete v tématu [ListBox – ovládací prvek](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="150f2-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 <span data-ttu-id="150f2-111">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="150f2-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="150f2-112">V Sběrač fragmentů kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="150f2-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="150f2-113">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="150f2-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="150f2-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="150f2-114">Compiling the Code</span></span>  
 <span data-ttu-id="150f2-115">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="150f2-115">This example requires:</span></span>  
  
-   <span data-ttu-id="150f2-116">Projekt odkazuje na System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="150f2-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="150f2-117">Přístup k členům <xref:System.Windows.Forms> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="150f2-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="150f2-118">Přidat `Imports` příkaz, pokud jste nejsou kvalifikující plně názvy členů v kódu.</span><span class="sxs-lookup"><span data-stu-id="150f2-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="150f2-119">Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="150f2-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="150f2-120">S svého formuláře <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="150f2-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="150f2-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="150f2-121">Robust Programming</span></span>  
 <span data-ttu-id="150f2-122">Není nutné použít <xref:System.Windows.Forms.ListBox> řízení, pokud chcete zobrazit názvy dostupné sériového portu.</span><span class="sxs-lookup"><span data-stu-id="150f2-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="150f2-123">Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="150f2-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="150f2-124">Pokud aplikace není nutné odpověď od uživatele, můžete použít <xref:System.Windows.Forms.TextBox> ovládací prvek pro zobrazení informací.</span><span class="sxs-lookup"><span data-stu-id="150f2-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="150f2-125">Názvy port vrácené `My.Computer.Ports.SerialPortNames` může být nesprávný při spuštění v systému Windows 98.</span><span class="sxs-lookup"><span data-stu-id="150f2-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="150f2-126">Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, například `Try...Catch...Finally` příkaz nebo `Using` při otevření portů pomocí názvu port.</span><span class="sxs-lookup"><span data-stu-id="150f2-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150f2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="150f2-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="150f2-128">Postupy: vytáčení modemů připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="150f2-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="150f2-129">Postupy: odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="150f2-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="150f2-130">Postupy: příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="150f2-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
