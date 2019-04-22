---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 33298fd9840630fbfd6f7f9d883cc2397a459843
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826441"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="0c821-102">Portové operace v rozhraní .NET Framework s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0c821-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="0c821-103">Přistupujete k sériovým portům počítače prostřednictvím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] tříd v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0c821-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0c821-104">Nejdůležitější třídy <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní založený na událostech vstupně-výstupních operací, přístup k PIN kódu a přerušení stavy a přístup k vlastnosti sériového portu ovladače.</span><span class="sxs-lookup"><span data-stu-id="0c821-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="0c821-105">Mohou být zabaleny do <xref:System.IO.Stream> objektu, přístupné prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0c821-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="0c821-106">Obtékání <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje přístup ke třídám, které používají datové proudy sériového portu.</span><span class="sxs-lookup"><span data-stu-id="0c821-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="0c821-107">Tento obor názvů zahrnuje výčty, které zjednodušují kontrolu nad sériových portů.</span><span class="sxs-lookup"><span data-stu-id="0c821-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="0c821-108">Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt je prostřednictvím <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0c821-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c821-109">Nemůžete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy přímý přístup k jiné typy portů, jako je například paralelní porty, portů USB a tak dále.</span><span class="sxs-lookup"><span data-stu-id="0c821-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="0c821-110">Výčty</span><span class="sxs-lookup"><span data-stu-id="0c821-110">Enumerations</span></span>  
 <span data-ttu-id="0c821-111">Tato tabulka uvádí a popisuje hlavní výčty použité pro přístup k sériového portu:</span><span class="sxs-lookup"><span data-stu-id="0c821-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="0c821-112">Výčet</span><span class="sxs-lookup"><span data-stu-id="0c821-112">Enumeration</span></span>|<span data-ttu-id="0c821-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0c821-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="0c821-114">Určuje ovládací prvek protokol použitý v navázání komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="0c821-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="0c821-115">Určuje bit parita pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="0c821-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="0c821-116">Určuje typ znaku, který uživateli přišel na sériového portu <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="0c821-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="0c821-117">Určuje chyby, ke kterým došlo u <xref:System.IO.Ports.SerialPort> objektu</span><span class="sxs-lookup"><span data-stu-id="0c821-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="0c821-118">Určuje typ změny, ke které došlo na <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="0c821-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="0c821-119">Určuje počet stop-bity na <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="0c821-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c821-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c821-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="0c821-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="0c821-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
