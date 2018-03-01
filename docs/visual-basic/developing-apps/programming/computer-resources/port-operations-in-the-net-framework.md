---
title: "Portové operace v rozhraní .NET Framework s jazykem Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77b8a464f2f64f701a5b99690756c0f22a410064
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a><span data-ttu-id="ceece-102">Portové operace v rozhraní .NET Framework s jazykem Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ceece-102">Port Operations in the .NET Framework with Visual Basic</span></span>
<span data-ttu-id="ceece-103">Přistupujete k sériovým portům počítače prostřednictvím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ceece-103">You can access your computer's serial ports through the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ceece-104">Nejdůležitější třída <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a událostmi řízené vstupně-výstupních operací, přístup k PIN kódu a zalomení stavy a přístup k vlastnostem sériového zařízení.</span><span class="sxs-lookup"><span data-stu-id="ceece-104">The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties.</span></span> <span data-ttu-id="ceece-105">Může být uzavřen do <xref:System.IO.Stream> objekt, přístupný prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ceece-105">It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property.</span></span> <span data-ttu-id="ceece-106">Zabalení <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje sériového portu, ke kterým přistupují třídy, které používají datových proudů.</span><span class="sxs-lookup"><span data-stu-id="ceece-106">Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams.</span></span> <span data-ttu-id="ceece-107">Obor názvů zahrnuje výčty, které zjednodušují ovládacího prvku sériových portů.</span><span class="sxs-lookup"><span data-stu-id="ceece-107">The namespace includes enumerations that simplify the control of serial ports.</span></span>  
  
 <span data-ttu-id="ceece-108">Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt je prostřednictvím <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ceece-108">The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceece-109">Nemůžete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy přímý přístup k jiné typy portů, jako je například paralelní porty, portů USB a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ceece-109">You cannot use [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes to directly access other types of ports, such as parallel ports, USB ports, and so on.</span></span>  
  
## <a name="enumerations"></a><span data-ttu-id="ceece-110">Výčty</span><span class="sxs-lookup"><span data-stu-id="ceece-110">Enumerations</span></span>  
 <span data-ttu-id="ceece-111">Tato tabulka uvádí a popisuje hlavní výčty použité pro přístup k sériového portu:</span><span class="sxs-lookup"><span data-stu-id="ceece-111">This table lists and describes the main enumerations used for accessing a serial port:</span></span>  
  
|<span data-ttu-id="ceece-112">Výčet</span><span class="sxs-lookup"><span data-stu-id="ceece-112">Enumeration</span></span>|<span data-ttu-id="ceece-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ceece-113">Description</span></span>|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|<span data-ttu-id="ceece-114">Určuje protokol ovládací prvek použitý v navazování komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="ceece-114">Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.Parity>|<span data-ttu-id="ceece-115">Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="ceece-115">Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialData>|<span data-ttu-id="ceece-116">Určuje typ znaku, který jste získali na sériového portu <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="ceece-116">Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.SerialError>|<span data-ttu-id="ceece-117">Určuje chyby, ke kterým došlo u <xref:System.IO.Ports.SerialPort> objektu</span><span class="sxs-lookup"><span data-stu-id="ceece-117">Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object</span></span>|  
|<xref:System.IO.Ports.SerialPinChange>|<span data-ttu-id="ceece-118">Určuje typ změny, které došlo <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="ceece-118">Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
|<xref:System.IO.Ports.StopBits>|<span data-ttu-id="ceece-119">Určuje počet stop-bity na <xref:System.IO.Ports.SerialPort> objektu.</span><span class="sxs-lookup"><span data-stu-id="ceece-119">Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ceece-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ceece-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="ceece-121">Přístup k portům počítače</span><span class="sxs-lookup"><span data-stu-id="ceece-121">Accessing the Computer's Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
