---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 936ff4c861444d3a971b38fd7b2a0af38b19494b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916593"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="67fed-102">Portové operace v rozhraní .NET Framework s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67fed-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="67fed-103">K sériovým portům počítače můžete přistupovat prostřednictvím tříd .NET Framework v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="67fed-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="67fed-104">Nejdůležitější třída <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače.</span><span class="sxs-lookup"><span data-stu-id="67fed-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="67fed-105">Může být zabalen do <xref:System.IO.Stream> objektu, který je přístupný <xref:System.IO.Ports.SerialPort.BaseStream> prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67fed-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="67fed-106"><xref:System.IO.Ports.SerialPort> Zabalením <xref:System.IO.Stream> do objektu umožníte, aby byl sériový port k dispozici třídám, které používají datové proudy.</span><span class="sxs-lookup"><span data-stu-id="67fed-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="67fed-107">Obor názvů obsahuje výčty, které zjednodušují řízení sériových portů.</span><span class="sxs-lookup"><span data-stu-id="67fed-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="67fed-108">Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt, je <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> prostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="67fed-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67fed-109">Třídy .NET Framework nemůžete použít k přímému přístupu k jiným typům portů, jako jsou paralelní porty, porty USB a tak dále.</span><span class="sxs-lookup"><span data-stu-id="67fed-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="67fed-110">Výčty</span><span class="sxs-lookup"><span data-stu-id="67fed-110">Enumerations</span></span>  
 <span data-ttu-id="67fed-111">Tato tabulka uvádí a popisuje hlavní výčty používané pro přístup k sériovému portu:</span><span class="sxs-lookup"><span data-stu-id="67fed-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="67fed-112">Výčet</span><span class="sxs-lookup"><span data-stu-id="67fed-112">Enumeration</span></span>|<span data-ttu-id="67fed-113">Popis</span><span class="sxs-lookup"><span data-stu-id="67fed-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="67fed-114">Určuje protokol řízení použitý při vytváření komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objekt.</span><span class="sxs-lookup"><span data-stu-id="67fed-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="67fed-115">Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objekt.</span><span class="sxs-lookup"><span data-stu-id="67fed-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="67fed-116">Určuje typ znaku, který byl přijat na sériovém portu <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="67fed-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="67fed-117">Určuje chyby, ke kterým dochází <xref:System.IO.Ports.SerialPort> u objektu.</span><span class="sxs-lookup"><span data-stu-id="67fed-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="67fed-118">Určuje typ změny, ke kterému došlo u <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="67fed-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="67fed-119">Určuje počet stop bitů použitých u <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="67fed-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67fed-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67fed-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="67fed-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="67fed-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
