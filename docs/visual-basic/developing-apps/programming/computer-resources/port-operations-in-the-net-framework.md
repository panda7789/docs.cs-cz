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
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic
K sériovým portům počítače můžete přistupovat prostřednictvím tříd .NET Framework v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů. Nejdůležitější třída <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a vstupně-výstupní operace řízené událostmi, přístup k stavům PIN a přerušení a přístup k vlastnostem sériového ovladače. Může být zabalen do <xref:System.IO.Stream> objektu, který je přístupný <xref:System.IO.Ports.SerialPort.BaseStream> prostřednictvím vlastnosti. <xref:System.IO.Ports.SerialPort> Zabalením <xref:System.IO.Stream> do objektu umožníte, aby byl sériový port k dispozici třídám, které používají datové proudy. Obor názvů obsahuje výčty, které zjednodušují řízení sériových portů.  
  
 Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt, je <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> prostřednictvím metody.  
  
> [!NOTE]
> Třídy .NET Framework nemůžete použít k přímému přístupu k jiným typům portů, jako jsou paralelní porty, porty USB a tak dále.  
  
## <a name="enumerations"></a>Výčty  
 Tato tabulka uvádí a popisuje hlavní výčty používané pro přístup k sériovému portu:  
  
|Výčet|Popis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Určuje protokol řízení použitý při vytváření komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objekt.|  
|<xref:System.IO.Ports.Parity>|Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objekt.|  
|<xref:System.IO.Ports.SerialData>|Určuje typ znaku, který byl přijat na sériovém portu <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.SerialError>|Určuje chyby, ke kterým dochází <xref:System.IO.Ports.SerialPort> u objektu.|  
|<xref:System.IO.Ports.SerialPinChange>|Určuje typ změny, ke kterému došlo u <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.StopBits>|Určuje počet stop bitů použitých u <xref:System.IO.Ports.SerialPort> objektu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
