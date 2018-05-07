---
title: Portové operace v rozhraní .NET Framework s jazykem Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
ms.openlocfilehash: 66b3729081540e8dede42556c58e44cd55b62666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic
Přistupujete k sériovým portům počítače prostřednictvím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů. Nejdůležitější třída <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a událostmi řízené vstupně-výstupních operací, přístup k PIN kódu a zalomení stavy a přístup k vlastnostem sériového zařízení. Může být uzavřen do <xref:System.IO.Stream> objekt, přístupný prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream> vlastnost. Zabalení <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje sériového portu, ke kterým přistupují třídy, které používají datových proudů. Obor názvů zahrnuje výčty, které zjednodušují ovládacího prvku sériových portů.  
  
 Nejjednodušší způsob, jak vytvořit <xref:System.IO.Ports.SerialPort> objekt je prostřednictvím <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A> metoda.  
  
> [!NOTE]
>  Nemůžete použít [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy přímý přístup k jiné typy portů, jako je například paralelní porty, portů USB a tak dále.  
  
## <a name="enumerations"></a>Výčty  
 Tato tabulka uvádí a popisuje hlavní výčty použité pro přístup k sériového portu:  
  
|Výčet|Popis|  
|---|---|   
|<xref:System.IO.Ports.Handshake>|Určuje protokol ovládací prvek použitý v navazování komunikace sériového portu pro <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.Parity>|Určuje paritní bit pro <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.SerialData>|Určuje typ znaku, který jste získali na sériového portu <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.SerialError>|Určuje chyby, ke kterým došlo u <xref:System.IO.Ports.SerialPort> objektu|  
|<xref:System.IO.Ports.SerialPinChange>|Určuje typ změny, které došlo <xref:System.IO.Ports.SerialPort> objektu.|  
|<xref:System.IO.Ports.StopBits>|Určuje počet stop-bity na <xref:System.IO.Ports.SerialPort> objektu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
