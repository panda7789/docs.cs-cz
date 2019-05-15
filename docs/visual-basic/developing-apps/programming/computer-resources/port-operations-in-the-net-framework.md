---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: e9927df7b646da6c66c11a5a686c4b038aaea774
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591367"
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic
Sériové porty počítače přístupné prostřednictvím třídy v rozhraní .NET Framework <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů. Nejdůležitější třídy <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní založený na událostech vstupně-výstupních operací, přístup k PIN kódu a přerušení stavy a přístup k vlastnosti sériového portu ovladače. Mohou být zabaleny do <xref:System.IO.Stream> objektu, přístupné prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream> vlastnost. Obtékání <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje přístup ke třídám, které používají datové proudy sériového portu. Tento obor názvů zahrnuje výčty, které zjednodušují kontrolu nad sériových portů.  
  
 Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt je prostřednictvím <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metody.  
  
> [!NOTE]
>  Třídy rozhraní .NET Framework nelze použít pro přímý přístup k jiné typy portů, jako je například paralelní porty, portů USB a tak dále.  
  
## <a name="enumerations"></a>Výčty  
 Tato tabulka uvádí a popisuje hlavní výčty použité pro přístup k sériového portu:  
  
|Výčet|Popis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Určuje ovládací prvek protokol použitý v navázání komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.Parity>|Určuje bit parita pro <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.SerialData>|Určuje typ znaku, který uživateli přišel na sériového portu <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.SerialError>|Určuje chyby, ke kterým došlo u <xref:System.IO.Ports.SerialPort> objektu|  
|<xref:System.IO.Ports.SerialPinChange>|Určuje typ změny, ke které došlo na <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.StopBits>|Určuje počet stop-bity na <xref:System.IO.Ports.SerialPort> objektu.|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
