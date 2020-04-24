---
title: 'Postupy: Příjem řetězců ze sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345602"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="ff278-102">Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff278-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>

<span data-ttu-id="ff278-103">Toto téma popisuje, jak používat `My.Computer.Ports` k přijímání řetězců ze sériových portů počítače v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ff278-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="ff278-104">Příjem řetězců ze sériového portu</span><span class="sxs-lookup"><span data-stu-id="ff278-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="ff278-105">Inicializujte návratový řetězec.</span><span class="sxs-lookup"><span data-stu-id="ff278-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="ff278-106">Určete, který sériový port by měl poskytnout řetězce.</span><span class="sxs-lookup"><span data-stu-id="ff278-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="ff278-107">Tento příklad předpokládá, že `COM1`je.</span><span class="sxs-lookup"><span data-stu-id="ff278-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="ff278-108">Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="ff278-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="ff278-109">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="ff278-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="ff278-110">`Try...Catch...Finally` Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="ff278-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="ff278-111">Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="ff278-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="ff278-112">Vytvoří `Do` smyčku pro čtení řádků textu, dokud nebudou k dispozici žádné další řádky.</span><span class="sxs-lookup"><span data-stu-id="ff278-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="ff278-113">Použijte <xref:System.IO.Ports.SerialPort.ReadLine> metodu pro čtení dalšího dostupného řádku textu ze sériového portu.</span><span class="sxs-lookup"><span data-stu-id="ff278-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="ff278-114">Použijte `If` příkaz k určení, <xref:System.IO.Ports.SerialPort.ReadLine> zda metoda vrátí `Nothing` (což znamená, že není k dispozici žádný další text).</span><span class="sxs-lookup"><span data-stu-id="ff278-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="ff278-115">Pokud se vrátí `Nothing`, ukončete `Do` smyčku.</span><span class="sxs-lookup"><span data-stu-id="ff278-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="ff278-116">Přidejte `Else` blok do `If` příkazu pro zpracování případu, pokud je řetězec skutečně čten.</span><span class="sxs-lookup"><span data-stu-id="ff278-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="ff278-117">Blok připojí řetězec ze sériového portu do návratového řetězce.</span><span class="sxs-lookup"><span data-stu-id="ff278-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="ff278-118">Vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="ff278-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="ff278-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff278-119">Example</span></span>  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="ff278-120">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ff278-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="ff278-121">Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="ff278-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="ff278-122">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="ff278-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ff278-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ff278-123">Compiling the Code</span></span>  

 <span data-ttu-id="ff278-124">V tomto příkladu se předpokládá, že `COM1`počítač používá.</span><span class="sxs-lookup"><span data-stu-id="ff278-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ff278-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ff278-125">Robust Programming</span></span>  

 <span data-ttu-id="ff278-126">V tomto příkladu se předpokládá, že `COM1`počítač používá.</span><span class="sxs-lookup"><span data-stu-id="ff278-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="ff278-127">Pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="ff278-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="ff278-128">Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="ff278-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="ff278-129">V `Try...Catch...Finally` tomto příkladu se používá blok k ujištění, že aplikace zavírá port a zachytává všechny výjimky časového limitu.</span><span class="sxs-lookup"><span data-stu-id="ff278-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="ff278-130">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ff278-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff278-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff278-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="ff278-132">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="ff278-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="ff278-133">Postupy: Posílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="ff278-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="ff278-134">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="ff278-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
