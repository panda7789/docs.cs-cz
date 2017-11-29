---
title: "Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6939dee58051e9a97fa704f063f35ff0ac440036
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="0edcb-102">Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0edcb-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="0edcb-103">Toto téma popisuje postup použití `My.Computer.Ports` pro příjem řetězců ze sériových portů počítače v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0edcb-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="0edcb-104">Pro příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="0edcb-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="0edcb-105">Inicializujte vrácený řetězec.</span><span class="sxs-lookup"><span data-stu-id="0edcb-105">Initialize the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  <span data-ttu-id="0edcb-106">Určete, které sériového portu by mělo poskytovat řetězce.</span><span class="sxs-lookup"><span data-stu-id="0edcb-106">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="0edcb-107">Tento příklad předpokládá, že je `COM1`.</span><span class="sxs-lookup"><span data-stu-id="0edcb-107">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="0edcb-108">Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="0edcb-108">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="0edcb-109">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="0edcb-109">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="0edcb-110">`Try...Catch...Finally` Bloku umožňuje aplikaci zavřete sériového portu i v případě, že vygeneruje výjimka.</span><span class="sxs-lookup"><span data-stu-id="0edcb-110">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="0edcb-111">Všechny kód, který zpracovává sériového portu musí nacházet v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="0edcb-111">All code that manipulates the serial port should appear within this block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="0edcb-112">Vytvoření `Do` smyčky pro čtení řádků textu, dokud nejsou k dispozici žádné další řádky.</span><span class="sxs-lookup"><span data-stu-id="0edcb-112">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  <span data-ttu-id="0edcb-113">Použití <xref:System.IO.Ports.SerialPort.ReadLine%2A> metoda přečíst další řádky textu z sériového portu.</span><span class="sxs-lookup"><span data-stu-id="0edcb-113">Use the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method to read the next available line of text from the serial port.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  <span data-ttu-id="0edcb-114">Použijte `If` příkaz k určení, zda <xref:System.IO.Ports.SerialPort.ReadLine%2A> metoda vrátí `Nothing` (což znamená žádný další text je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="0edcb-114">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="0edcb-115">Pokud vrátit `Nothing`, ukončete `Do` smyčky.</span><span class="sxs-lookup"><span data-stu-id="0edcb-115">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  <span data-ttu-id="0edcb-116">Přidat `Else` zablokujte `If` příkaz k zpracování případu, pokud je řetězec ve skutečnosti pro čtení.</span><span class="sxs-lookup"><span data-stu-id="0edcb-116">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="0edcb-117">Blok připojí řetězec z sériového portu, který má návratový řetězec.</span><span class="sxs-lookup"><span data-stu-id="0edcb-117">The block appends the string from the serial port to the return string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  <span data-ttu-id="0edcb-118">Vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="0edcb-118">Return the string.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="0edcb-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="0edcb-119">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 <span data-ttu-id="0edcb-120">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="0edcb-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="0edcb-121">V Sběrač fragmentů kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="0edcb-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="0edcb-122">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="0edcb-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0edcb-123">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0edcb-123">Compiling the Code</span></span>  
 <span data-ttu-id="0edcb-124">Tento příklad předpokládá, že počítač používá `COM1`.</span><span class="sxs-lookup"><span data-stu-id="0edcb-124">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="0edcb-125">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="0edcb-125">Robust Programming</span></span>  
 <span data-ttu-id="0edcb-126">Tento příklad předpokládá, že počítač používá `COM1`.</span><span class="sxs-lookup"><span data-stu-id="0edcb-126">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="0edcb-127">Pro větší flexibilitu by měl kód umožnit uživateli vybrat ze seznamu dostupných portů požadovaných sériového portu.</span><span class="sxs-lookup"><span data-stu-id="0edcb-127">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="0edcb-128">Další informace najdete v tématu [postupy: zobrazení k dispozici sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="0edcb-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="0edcb-129">Tento příklad používá `Try...Catch...Finally` bloku, abyste měli jistotu, že aplikace zavře port a zachytával všechny výjimky časový limit.</span><span class="sxs-lookup"><span data-stu-id="0edcb-129">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="0edcb-130">Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0edcb-130">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edcb-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0edcb-131">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="0edcb-132">Postupy: vytáčení modemů připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="0edcb-132">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="0edcb-133">Postupy: odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="0edcb-133">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="0edcb-134">Postupy: zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="0edcb-134">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
