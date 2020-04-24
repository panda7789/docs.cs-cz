---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345641"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="349cc-102">Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="349cc-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="349cc-103">Toto téma popisuje, jak použít `My.Computer.Ports` k vytočení modemu v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="349cc-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="349cc-104">Modem je obvykle připojen k jednomu ze sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="349cc-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="349cc-105">Aby vaše aplikace komunikovala s modemem, musí odeslat příkazy do příslušného sériového portu.</span><span class="sxs-lookup"><span data-stu-id="349cc-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="349cc-106">Vytočit modem</span><span class="sxs-lookup"><span data-stu-id="349cc-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="349cc-107">Určete, ke kterému sériovému portu je modem připojen.</span><span class="sxs-lookup"><span data-stu-id="349cc-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="349cc-108">Tento příklad předpokládá, že je modem na portu COM1.</span><span class="sxs-lookup"><span data-stu-id="349cc-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="349cc-109">Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="349cc-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="349cc-110">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="349cc-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="349cc-111">`Using` Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="349cc-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="349cc-112">Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo `Try...Catch...Finally` v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="349cc-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="349cc-113">Nastavte `DtrEnable` vlastnost tak, aby označovala, že je počítač připravený přijmout příchozí přenos z modemu.</span><span class="sxs-lookup"><span data-stu-id="349cc-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="349cc-114">Odešlete příkaz k vytočení a telefonní číslo modemu přes sériový port pomocí <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="349cc-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="349cc-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="349cc-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="349cc-116">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="349cc-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="349cc-117">Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="349cc-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="349cc-118">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="349cc-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="349cc-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="349cc-119">Compiling the Code</span></span>  

 <span data-ttu-id="349cc-120">Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="349cc-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="349cc-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="349cc-121">Robust Programming</span></span>  

 <span data-ttu-id="349cc-122">Tento příklad předpokládá, že modem je připojen k portu COM1.</span><span class="sxs-lookup"><span data-stu-id="349cc-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="349cc-123">Doporučujeme, aby váš kód mohl uživateli vybrat požadovaný sériový port ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="349cc-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="349cc-124">Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="349cc-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="349cc-125">Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="349cc-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="349cc-126">Další informace naleznete v tématu [using – příkaz](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="349cc-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="349cc-127">V tomto příkladu aplikace po připojení modemu odpojí sériový port.</span><span class="sxs-lookup"><span data-stu-id="349cc-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="349cc-128">Realisticky budete chtít přenést data do a z modemu.</span><span class="sxs-lookup"><span data-stu-id="349cc-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="349cc-129">Další informace najdete v tématu [Postupy: příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="349cc-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="349cc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="349cc-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="349cc-131">Postupy: Posílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="349cc-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="349cc-132">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="349cc-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="349cc-133">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="349cc-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
