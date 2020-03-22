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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic

K sériovým portům počítače můžete přistupovat prostřednictvím <xref:System.IO.Ports?displayProperty=nameWithType> tříd rozhraní .NET Framework v oboru názvů. Nejdůležitější třída , <xref:System.IO.Ports.SerialPort>poskytuje rozhraní pro synchronní a událostmi řízené vstupně-up, přístup ke stavům pin a break a přístup k vlastnostem sériového ovladače. Může být zabalen do <xref:System.IO.Stream> objektu, <xref:System.IO.Ports.SerialPort.BaseStream> přístupné prostřednictvím vlastnosti. Obtékání <xref:System.IO.Ports.SerialPort> objektu <xref:System.IO.Stream> umožňuje přístup k sériovému portu pomocí tříd, které používají datové proudy. Obor názvů obsahuje výčty, které zjednodušují řízení sériových portů.

Nejjednodušší způsob, jak <xref:System.IO.Ports.SerialPort> vytvořit objekt <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> je prostřednictvím metody.

> [!NOTE]
> Třídy rozhraní .NET Framework nelze použít k přímému přístupu k jiným typům portů, jako jsou paralelní porty, porty USB a tak dále.

## <a name="enumerations"></a>Výčty

Tato tabulka uvádí a popisuje hlavní výčty používané pro přístup k sériovému portu:

|Výčet|Popis|
|---|---|
|<xref:System.IO.Ports.Handshake>|Určuje řídicí protokol používaný při navazování komunikace <xref:System.IO.Ports.SerialPort> sériového portu pro objekt.|
|<xref:System.IO.Ports.Parity>|Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objekt.|
|<xref:System.IO.Ports.SerialData>|Určuje typ znaku, který byl přijat na <xref:System.IO.Ports.SerialPort> sériovém portu objektu.|
|<xref:System.IO.Ports.SerialError>|Určuje chyby, ke <xref:System.IO.Ports.SerialPort> kterým dochází u objektu.|
|<xref:System.IO.Ports.SerialPinChange>|Určuje typ změny, ke které <xref:System.IO.Ports.SerialPort> došlo u objektu.|
|<xref:System.IO.Ports.StopBits>|Určuje počet stopbitů použitých <xref:System.IO.Ports.SerialPort> na objektu.|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
