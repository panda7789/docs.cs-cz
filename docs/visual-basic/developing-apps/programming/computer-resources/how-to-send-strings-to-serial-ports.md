---
title: 'Postupy: Posílání řetězců na sériové porty'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360290"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="b524a-102">Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b524a-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>

<span data-ttu-id="b524a-103">V tomto tématu se dozvíte, jak pomocí nástroje `My.Computer.Ports` odesílat řetězce na sériové porty počítače v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b524a-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b524a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b524a-104">Example</span></span>  

 <span data-ttu-id="b524a-105">Tento příklad odešle řetězec na sériový port COM1.</span><span class="sxs-lookup"><span data-stu-id="b524a-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="b524a-106">V počítači možná budete muset použít jiný sériový port.</span><span class="sxs-lookup"><span data-stu-id="b524a-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="b524a-107">Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="b524a-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="b524a-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="b524a-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="b524a-109">`Using`Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="b524a-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="b524a-110">Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="b524a-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="b524a-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A>Metoda odesílá data do sériového portu.</span><span class="sxs-lookup"><span data-stu-id="b524a-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b524a-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b524a-112">Compiling the Code</span></span>  
  
- <span data-ttu-id="b524a-113">V tomto příkladu se předpokládá, že počítač používá `COM1` .</span><span class="sxs-lookup"><span data-stu-id="b524a-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b524a-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b524a-114">Robust Programming</span></span>  

 <span data-ttu-id="b524a-115">Tento příklad předpokládá, že počítač používá `COM1` ; pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="b524a-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="b524a-116">Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="b524a-116">For more information, see [How to: Show Available Serial Ports](how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="b524a-117">Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b524a-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="b524a-118">Další informace naleznete v tématu [using – příkaz](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b524a-118">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b524a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="b524a-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="b524a-120">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="b524a-120">How to: Dial Modems Attached to Serial Ports</span></span>](how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="b524a-121">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="b524a-121">How to: Show Available Serial Ports</span></span>](how-to-show-available-serial-ports.md)
