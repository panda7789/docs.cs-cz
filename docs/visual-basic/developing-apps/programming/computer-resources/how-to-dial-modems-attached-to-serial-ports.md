---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db482af7750012d8805d4f834063a2c82224cf67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337029"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="473f0-102">Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="473f0-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="473f0-103">Toto téma popisuje způsob použití `My.Computer.Ports` vytáčení modemů v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="473f0-103">This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.</span></span>  
  
 <span data-ttu-id="473f0-104">Obvykle modemu je připojený k jednomu ze sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="473f0-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="473f0-105">Pro vaši aplikaci ke komunikaci s modemem se musí odesílat příkazy na odpovídající sériového portu.</span><span class="sxs-lookup"><span data-stu-id="473f0-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="473f0-106">Chcete-li vytočte modemu</span><span class="sxs-lookup"><span data-stu-id="473f0-106">To dial a modem</span></span>  
  
1. <span data-ttu-id="473f0-107">Určete, které sériového portu, který je připojen k.</span><span class="sxs-lookup"><span data-stu-id="473f0-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="473f0-108">Tento příklad předpokládá, že je zapnutý COM1 modem.</span><span class="sxs-lookup"><span data-stu-id="473f0-108">This example assumes the modem is on COM1.</span></span>  
  
2. <span data-ttu-id="473f0-109">Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="473f0-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="473f0-110">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="473f0-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="473f0-111">`Using` Bloku umožňuje, aby aplikace zavřete sériového portu, i v případě, že vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="473f0-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="473f0-112">Veškerý kód, který provádí úpravy sériového portu by se měla objevit v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="473f0-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. <span data-ttu-id="473f0-113">Nastavte `DtrEnable` vlastnost umožňující označit, že je počítač připravený k přijetí příchozího přenosu od modemu.</span><span class="sxs-lookup"><span data-stu-id="473f0-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. <span data-ttu-id="473f0-114">Odeslat volání příkazu a telefonní číslo přes sériový port prostřednictvím modemu <xref:System.IO.Ports.SerialPort.Write%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="473f0-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="473f0-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="473f0-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 <span data-ttu-id="473f0-116">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="473f0-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="473f0-117">V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="473f0-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="473f0-118">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="473f0-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="473f0-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="473f0-119">Compiling the Code</span></span>  
 <span data-ttu-id="473f0-120">Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="473f0-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="473f0-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="473f0-121">Robust Programming</span></span>  
 <span data-ttu-id="473f0-122">Tento příklad předpokládá, že je připojen k COM1.</span><span class="sxs-lookup"><span data-stu-id="473f0-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="473f0-123">Doporučujeme vám, že váš kód umožnit uživateli vybrat požadovanou sériového portu ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="473f0-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="473f0-124">Další informace najdete v tématu [jak: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="473f0-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="473f0-125">Tento příklad používá `Using` blok k Ujistěte se, že aplikace zavře portu i v případě, že dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="473f0-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="473f0-126">Další informace najdete v tématu [příkazu Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="473f0-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="473f0-127">V tomto příkladu aplikace odpojí sériového portu po vytočí modemu.</span><span class="sxs-lookup"><span data-stu-id="473f0-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="473f0-128">Reálně můžete k přenosu dat do a z modemu.</span><span class="sxs-lookup"><span data-stu-id="473f0-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="473f0-129">Další informace najdete v tématu [jak: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="473f0-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473f0-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="473f0-130">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="473f0-131">Postupy: Odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="473f0-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="473f0-132">Postupy: Příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="473f0-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [<span data-ttu-id="473f0-133">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="473f0-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
