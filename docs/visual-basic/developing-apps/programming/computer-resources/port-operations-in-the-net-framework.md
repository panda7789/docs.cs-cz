---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 33298fd9840630fbfd6f7f9d883cc2397a459843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921404"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="9cd0b-102">Portové operace v rozhraní .NET Framework s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9cd0b-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="9cd0b-103">Přistupujete k sériovým portům počítače prostřednictvím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tříd v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="9cd0b-104">Nejdůležitější třídy <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní založený na událostech vstupně-výstupních operací, přístup k PIN kódu a přerušení stavy a přístup k vlastnosti sériového portu ovladače.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="9cd0b-105">Mohou být zabaleny do <xref:System.IO.Stream> objektu, přístupné prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="9cd0b-106">Obtékání <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje přístup ke třídám, které používají datové proudy sériového portu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="9cd0b-107">Tento obor názvů zahrnuje výčty, které zjednodušují kontrolu nad sériových portů.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="9cd0b-108">Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt je prostřednictvím <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cd0b-109">Nemůžete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy přímý přístup k jiné typy portů, jako je například paralelní porty, portů USB a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="9cd0b-110">Výčty</span><span class="sxs-lookup"><span data-stu-id="9cd0b-110">Enumerations</span></span>  
 <span data-ttu-id="9cd0b-111">Tato tabulka uvádí a popisuje hlavní výčty použité pro přístup k sériového portu:</span><span class="sxs-lookup"><span data-stu-id="9cd0b-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="9cd0b-112">Výčet</span><span class="sxs-lookup"><span data-stu-id="9cd0b-112">Enumeration</span></span>|<span data-ttu-id="9cd0b-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9cd0b-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="9cd0b-114">Určuje ovládací prvek protokol použitý v navázání komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="9cd0b-115">Určuje bit parita pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="9cd0b-116">Určuje typ znaku, který uživateli přišel na sériového portu <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="9cd0b-117">Určuje chyby, ke kterým došlo u <xref:System.IO.Ports.SerialPort> objektu</span><span class="sxs-lookup"><span data-stu-id="9cd0b-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="9cd0b-118">Určuje typ změny, ke které došlo na <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="9cd0b-119">Určuje počet stop-bity na <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="9cd0b-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9cd0b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cd0b-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="9cd0b-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="9cd0b-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
