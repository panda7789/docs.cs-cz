---
title: "Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea1b2d6152af8919ac1aa272def4ba198b33867c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="7b2f3-102">Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b2f3-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="7b2f3-103">Toto téma popisuje postup použití `My.Computer.Ports` k vytáčení modemu v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b2f3-103">This topic describes how to use `My.Computer.Ports` to dial a modem in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="7b2f3-104">Obvykle je modemu připojené k jednomu ze sériových portů v počítači.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="7b2f3-105">Pro aplikace komunikovat s modem se musí odesílat příkazy k příslušnému sériového portu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="7b2f3-106">K vytáčení modemu</span><span class="sxs-lookup"><span data-stu-id="7b2f3-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="7b2f3-107">Určí, které sériového portu, který je připojen k.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="7b2f3-108">Tento příklad předpokládá, že je zapnutý COM1 modem.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="7b2f3-109">Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="7b2f3-110">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="7b2f3-111">`Using` Bloku umožňuje aplikaci zavřete sériového portu i v případě, že vygeneruje výjimka.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="7b2f3-112">Všechny kód, který zpracovává sériového portu by se měla objevit v rámci tohoto bloku nebo uvnitř `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  <span data-ttu-id="7b2f3-113">Nastavte `DtrEnable` vlastnost k označení, že je počítač připraven k přijetí příchozího přenosu z modemu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-113">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  <span data-ttu-id="7b2f3-114">Příkaz dial a telefonní číslo poslat modemu prostřednictvím sériového portu prostřednictvím <xref:System.IO.Ports.SerialPort.Write%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-114">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="7b2f3-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b2f3-115">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 <span data-ttu-id="7b2f3-116">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-116">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7b2f3-117">V Sběrač fragmentů kódu je umístěn v **připojení a sítě**.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-117">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="7b2f3-118">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="7b2f3-118">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b2f3-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7b2f3-119">Compiling the Code</span></span>  
 <span data-ttu-id="7b2f3-120">Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-120">This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7b2f3-121">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="7b2f3-121">Robust Programming</span></span>  
 <span data-ttu-id="7b2f3-122">Tento příklad předpokládá, že je připojen k COM1.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-122">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="7b2f3-123">Doporučujeme vám, že váš kód umožňují uživateli vybrat ze seznamu dostupných portů požadovaných sériového portu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-123">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="7b2f3-124">Další informace najdete v tématu [postupy: zobrazení k dispozici sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="7b2f3-124">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="7b2f3-125">Tento příklad používá `Using` bloku a ujistěte se, že aplikace zavře port i v případě, že vyhodí výjimku.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-125">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="7b2f3-126">Další informace najdete v tématu [pomocí příkazu](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7b2f3-126">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="7b2f3-127">V tomto příkladu aplikace odpojí sériového portu po vytočení modemu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-127">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="7b2f3-128">Reálně můžete k přenosu dat do a z modemu.</span><span class="sxs-lookup"><span data-stu-id="7b2f3-128">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="7b2f3-129">Další informace najdete v tématu [postupy: příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="7b2f3-129">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2f3-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b2f3-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="7b2f3-131">Postupy: odesílání řetězců na sériové porty</span><span class="sxs-lookup"><span data-stu-id="7b2f3-131">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="7b2f3-132">Postupy: příjem řetězců ze sériových portů</span><span class="sxs-lookup"><span data-stu-id="7b2f3-132">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [<span data-ttu-id="7b2f3-133">Postupy: zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="7b2f3-133">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
