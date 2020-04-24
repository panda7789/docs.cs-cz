---
title: 'Postupy: Posílání řetězců na sériové porty'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345590"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="4550e-102">Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4550e-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="4550e-103">V tomto tématu se dozvíte `My.Computer.Ports` , jak pomocí nástroje odesílat řetězce na sériové porty počítače v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4550e-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4550e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4550e-104">Example</span></span>  

 <span data-ttu-id="4550e-105">Tento příklad odešle řetězec na sériový port COM1.</span><span class="sxs-lookup"><span data-stu-id="4550e-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="4550e-106">V počítači možná budete muset použít jiný sériový port.</span><span class="sxs-lookup"><span data-stu-id="4550e-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="4550e-107">Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="4550e-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="4550e-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="4550e-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="4550e-109">`Using` Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="4550e-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="4550e-110">Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku `Try...Catch...Finally` nebo v rámci bloku.</span><span class="sxs-lookup"><span data-stu-id="4550e-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="4550e-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda odesílá data do sériového portu.</span><span class="sxs-lookup"><span data-stu-id="4550e-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4550e-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4550e-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="4550e-113">V tomto příkladu se předpokládá, že `COM1`počítač používá.</span><span class="sxs-lookup"><span data-stu-id="4550e-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4550e-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4550e-114">Robust Programming</span></span>  

 <span data-ttu-id="4550e-115">Tento příklad předpokládá, že počítač používá `COM1`; pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="4550e-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="4550e-116">Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="4550e-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="4550e-117">Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="4550e-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="4550e-118">Další informace naleznete v tématu [using – příkaz](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4550e-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4550e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4550e-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="4550e-120">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="4550e-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="4550e-121">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="4550e-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
