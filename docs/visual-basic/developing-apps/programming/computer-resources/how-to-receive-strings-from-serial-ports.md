---
title: 'Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 6c832cd9ef5df904850261f4de2d769bfc28c3cb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296716"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="fee54-102">Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fee54-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="fee54-103">Toto téma popisuje způsob použití `My.Computer.Ports` pro příjem řetězců ze sériových portů počítače v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fee54-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in Visual Basic.</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="fee54-104">Pro příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="fee54-104">To receive strings from the serial port</span></span>  
  
1. <span data-ttu-id="fee54-105">Inicializujte vráceného řetězce.</span><span class="sxs-lookup"><span data-stu-id="fee54-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. <span data-ttu-id="fee54-106">Určení, které sériového portu by měla poskytnout řetězce.</span><span class="sxs-lookup"><span data-stu-id="fee54-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="fee54-107">Tento příklad předpokládá, že je `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fee54-107">This example assumes it is `COM1`.</span></span>  
  
3. <span data-ttu-id="fee54-108">Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="fee54-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="fee54-109">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="fee54-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="fee54-110">`Try...Catch...Finally` Bloku umožňuje, aby aplikace zavřete sériového portu, i v případě, že vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="fee54-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="fee54-111">Veškerý kód, který provádí úpravy sériového portu by se zobrazit v rámci tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="fee54-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. <span data-ttu-id="fee54-112">Vytvoření `Do` smyčky pro čtení řádků textu, dokud nejsou k dispozici žádné další řádky.</span><span class="sxs-lookup"><span data-stu-id="fee54-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. <span data-ttu-id="fee54-113">Použití <xref:System.IO.Ports.SerialPort.ReadLine> metodu za účelem čtení další dostupný řádek textu ze sériového portu.</span><span class="sxs-lookup"><span data-stu-id="fee54-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. <span data-ttu-id="fee54-114">Použití `If` příkaz k určení, zda <xref:System.IO.Ports.SerialPort.ReadLine> vrátí metoda `Nothing` (což znamená, že žádné další text je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="fee54-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="fee54-115">Pokud se nevrátí `Nothing`, ukončete `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="fee54-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. <span data-ttu-id="fee54-116">Přidat `Else` bloku `If` příkaz pro zpracování případu, pokud je ve skutečnosti čtení řetězce.</span><span class="sxs-lookup"><span data-stu-id="fee54-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="fee54-117">Blok připojí řetězec ze sériového portu, který má vráceného řetězce.</span><span class="sxs-lookup"><span data-stu-id="fee54-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. <span data-ttu-id="fee54-118">Vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="fee54-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a><span data-ttu-id="fee54-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="fee54-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 <span data-ttu-id="fee54-120">Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="fee54-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="fee54-121">V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="fee54-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="fee54-122">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="fee54-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fee54-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fee54-123">Compiling the Code</span></span>  
 <span data-ttu-id="fee54-124">Tento příklad předpokládá, že počítač používá `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fee54-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fee54-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="fee54-125">Robust Programming</span></span>  
 <span data-ttu-id="fee54-126">Tento příklad předpokládá, že počítač používá `COM1`.</span><span class="sxs-lookup"><span data-stu-id="fee54-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="fee54-127">Pro větší flexibilitu by měl kód umožnit uživateli vybrat požadovanou sériového portu ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="fee54-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="fee54-128">Další informace najdete v tématu [jak: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="fee54-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="fee54-129">Tento příklad používá `Try...Catch...Finally` blok k Ujistěte se, že aplikace zavře port a zachytit žádné výjimky časového limitu.</span><span class="sxs-lookup"><span data-stu-id="fee54-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="fee54-130">Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fee54-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee54-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fee54-131">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="fee54-132">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="fee54-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="fee54-133">Postupy: Odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="fee54-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="fee54-134">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="fee54-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
