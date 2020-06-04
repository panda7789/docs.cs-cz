---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: e55ce6399dae435fbd5b2f730d4d0848c98d8955
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363264"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="a7997-102">Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7997-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="a7997-103">Toto téma popisuje, jak použít `My.Computer.Ports` k vytočení modemu v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7997-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="a7997-104">Modem je obvykle připojen k jednomu ze sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="a7997-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="a7997-105">Aby vaše aplikace komunikovala s modemem, musí odeslat příkazy do příslušného sériového portu.</span><span class="sxs-lookup"><span data-stu-id="a7997-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="a7997-106">Vytočit modem</span><span class="sxs-lookup"><span data-stu-id="a7997-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="a7997-107">Určete, ke kterému sériovému portu je modem připojen.</span><span class="sxs-lookup"><span data-stu-id="a7997-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="a7997-108">Tento příklad předpokládá, že je modem na portu COM1.</span><span class="sxs-lookup"><span data-stu-id="a7997-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="a7997-109">Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="a7997-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="a7997-110">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7997-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="a7997-111">`Using`Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="a7997-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="a7997-112">Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="a7997-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="a7997-113">Nastavte `DtrEnable` vlastnost tak, aby označovala, že je počítač připravený přijmout příchozí přenos z modemu.</span><span class="sxs-lookup"><span data-stu-id="a7997-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="a7997-114">Odešlete příkaz k vytočení a telefonní číslo modemu přes sériový port pomocí <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a7997-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="a7997-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7997-115">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="a7997-116">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a7997-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="a7997-117">Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="a7997-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="a7997-118">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="a7997-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a7997-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a7997-119">Compiling the Code</span></span>  

 <span data-ttu-id="a7997-120">Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a7997-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a7997-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="a7997-121">Robust Programming</span></span>  

 <span data-ttu-id="a7997-122">Tento příklad předpokládá, že modem je připojen k portu COM1.</span><span class="sxs-lookup"><span data-stu-id="a7997-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="a7997-123">Doporučujeme, aby váš kód mohl uživateli vybrat požadovaný sériový port ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="a7997-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="a7997-124">Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a7997-124">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="a7997-125">Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="a7997-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="a7997-126">Další informace naleznete v tématu [using – příkaz](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a7997-126">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="a7997-127">V tomto příkladu aplikace po připojení modemu odpojí sériový port.</span><span class="sxs-lookup"><span data-stu-id="a7997-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="a7997-128">Realisticky budete chtít přenést data do a z modemu.</span><span class="sxs-lookup"><span data-stu-id="a7997-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="a7997-129">Další informace najdete v tématu [Postupy: příjem řetězců ze sériových portů](how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="a7997-129">For more information, see [How to: Receive Strings From Serial Ports](how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7997-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7997-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="a7997-131">Postupy: Posílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="a7997-131">How to: Send Strings to Serial Ports</span></span>](how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="a7997-132">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="a7997-132">How to: Receive Strings From Serial Ports</span></span>](how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="a7997-133">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="a7997-133">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
