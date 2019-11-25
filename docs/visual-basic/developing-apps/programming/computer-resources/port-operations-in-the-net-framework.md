---
title: Portové operace v rozhraní .NET Framework
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 68f0c67b8135c6bb7ce8a134e2a324bc12c0aad9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345508"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic

You can access your computer's serial ports through the .NET Framework classes in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace. The most important class, <xref:System.IO.Ports.SerialPort>, provides a framework for synchronous and event-driven I/O, access to pin and break states, and access to serial driver properties. It can be wrapped in a <xref:System.IO.Stream> object, accessible through the <xref:System.IO.Ports.SerialPort.BaseStream> property. Wrapping <xref:System.IO.Ports.SerialPort> in a <xref:System.IO.Stream> object allows the serial port to be accessed by classes that use streams. The namespace includes enumerations that simplify the control of serial ports.

The simplest way to create a <xref:System.IO.Ports.SerialPort> object is through the <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> method.

> [!NOTE]
> You cannot use .NET Framework classes to directly access other types of ports, such as parallel ports, USB ports, and so on.

## <a name="enumerations"></a>Výčty

This table lists and describes the main enumerations used for accessing a serial port:

|Výčet|Popis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Specifies the control protocol used in establishing a serial port communication for a <xref:System.IO.Ports.SerialPort> object.|
|<xref:System.IO.Ports.Parity>|Specifies the parity bit for a <xref:System.IO.Ports.SerialPort> object.|
|<xref:System.IO.Ports.SerialData>|Specifies the type of character that was received on the serial port of the <xref:System.IO.Ports.SerialPort> object.|
|<xref:System.IO.Ports.SerialError>|Specifies errors that occur on the <xref:System.IO.Ports.SerialPort> object|
|<xref:System.IO.Ports.SerialPinChange>|Specifies the type of change that occurred on the <xref:System.IO.Ports.SerialPort> object.|
|<xref:System.IO.Ports.StopBits>|Specifies the number of stop bits used on the <xref:System.IO.Ports.SerialPort> object.|

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
