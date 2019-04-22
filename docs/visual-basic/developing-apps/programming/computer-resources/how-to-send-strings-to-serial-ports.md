---
title: 'Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: e1f0c9d5ba428f5379f8025c0e733cdbeb5204e0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822853"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="d627d-102">Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d627d-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="d627d-103">Toto téma popisuje způsob použití `My.Computer.Ports` k odesílání řetězců na sériové porty počítače v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d627d-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d627d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d627d-104">Example</span></span>  
 <span data-ttu-id="d627d-105">Tento příklad odešle řetězec COM1 sériového portu.</span><span class="sxs-lookup"><span data-stu-id="d627d-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="d627d-106">Budete muset použít jiné sériového portu ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d627d-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="d627d-107">Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port.</span><span class="sxs-lookup"><span data-stu-id="d627d-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="d627d-108">Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d627d-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="d627d-109">`Using` Bloku umožňuje, aby aplikace zavřete sériového portu, i v případě, že vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="d627d-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="d627d-110">Veškerý kód, který provádí úpravy sériového portu by se měla objevit v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="d627d-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="d627d-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda odesílá data do sériového portu.</span><span class="sxs-lookup"><span data-stu-id="d627d-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d627d-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d627d-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d627d-113">Tento příklad předpokládá, že počítač používá `COM1`.</span><span class="sxs-lookup"><span data-stu-id="d627d-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d627d-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d627d-114">Robust Programming</span></span>  
 <span data-ttu-id="d627d-115">Tento příklad předpokládá, že počítač používá `COM1`; pro větší flexibilitu, kód by měl umožnit uživateli vybrat požadovanou sériového portu ze seznamu dostupných portů.</span><span class="sxs-lookup"><span data-stu-id="d627d-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="d627d-116">Další informace najdete v tématu [jak: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="d627d-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="d627d-117">Tento příklad používá `Using` blok k Ujistěte se, že aplikace zavře portu i v případě, že dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="d627d-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="d627d-118">Další informace najdete v tématu [příkazu Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d627d-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d627d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d627d-119">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [<span data-ttu-id="d627d-120">Postupy: Vytáčení čísel na modemech připojených k sériovým portům</span><span class="sxs-lookup"><span data-stu-id="d627d-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="d627d-121">Postupy: Zobrazení dostupných sériových portů</span><span class="sxs-lookup"><span data-stu-id="d627d-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
