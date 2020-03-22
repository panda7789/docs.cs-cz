---
title: Portové operace v rozhraní .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345508"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="45848-102">Portové operace v rozhraní .NET Framework s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45848-102">Port Operations in the .NET Framework with Visual Basic</span></span>

<span data-ttu-id="45848-103">K sériovým portům počítače můžete přistupovat prostřednictvím <xref:System.IO.Ports?displayProperty=nameWithType> tříd rozhraní .NET Framework v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="45848-103">You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="45848-104">Nejdůležitější třída , <xref:System.IO.Ports.SerialPort>poskytuje rozhraní pro synchronní a událostmi řízené vstupně-up, přístup ke stavům pin a break a přístup k vlastnostem sériového ovladače.</span><span class="sxs-lookup"><span data-stu-id="45848-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="45848-105">Může být zabalen do <xref:System.IO.Stream> objektu, <xref:System.IO.Ports.SerialPort.BaseStream> přístupné prostřednictvím vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="45848-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="45848-106">Obtékání <xref:System.IO.Ports.SerialPort> objektu <xref:System.IO.Stream> umožňuje přístup k sériovému portu pomocí tříd, které používají datové proudy.</span><span class="sxs-lookup"><span data-stu-id="45848-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="45848-107">Obor názvů obsahuje výčty, které zjednodušují řízení sériových portů.</span><span class="sxs-lookup"><span data-stu-id="45848-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>

<span data-ttu-id="45848-108">Nejjednodušší způsob, jak <xref:System.IO.Ports.SerialPort> vytvořit objekt <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> je prostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="45848-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="45848-109">Třídy rozhraní .NET Framework nelze použít k přímému přístupu k jiným typům portů, jako jsou paralelní porty, porty USB a tak dále.</span><span class="sxs-lookup"><span data-stu-id="45848-109">You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>

## <a name="enumerations"></a><span data-ttu-id="45848-110">Výčty</span><span class="sxs-lookup"><span data-stu-id="45848-110">Enumerations</span></span>

<span data-ttu-id="45848-111">Tato tabulka uvádí a popisuje hlavní výčty používané pro přístup k sériovému portu:</span><span class="sxs-lookup"><span data-stu-id="45848-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>

|<span data-ttu-id="45848-112">Výčet</span><span class="sxs-lookup"><span data-stu-id="45848-112">Enumeration</span></span>|<span data-ttu-id="45848-113">Popis</span><span class="sxs-lookup"><span data-stu-id="45848-113">Description</span></span>|
|---|---|
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="45848-114">Určuje řídicí protokol používaný při navazování komunikace <xref:System.IO.Ports.SerialPort> sériového portu pro objekt.</span><span class="sxs-lookup"><span data-stu-id="45848-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="45848-115">Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objekt.</span><span class="sxs-lookup"><span data-stu-id="45848-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="45848-116">Určuje typ znaku, který byl přijat na <xref:System.IO.Ports.SerialPort> sériovém portu objektu.</span><span class="sxs-lookup"><span data-stu-id="45848-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="45848-117">Určuje chyby, ke <xref:System.IO.Ports.SerialPort> kterým dochází u objektu.</span><span class="sxs-lookup"><span data-stu-id="45848-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="45848-118">Určuje typ změny, ke které <xref:System.IO.Ports.SerialPort> došlo u objektu.</span><span class="sxs-lookup"><span data-stu-id="45848-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="45848-119">Určuje počet stopbitů použitých <xref:System.IO.Ports.SerialPort> na objektu.</span><span class="sxs-lookup"><span data-stu-id="45848-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|

## <a name="see-also"></a><span data-ttu-id="45848-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="45848-120">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="45848-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="45848-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
