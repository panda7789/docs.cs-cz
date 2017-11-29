---
title: "Portové operace v rozhraní .NET Framework s jazykem Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: ports, Visual Basic
ms.assetid: 1eba223b-7bd3-401a-b097-982bce96df1b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8db016461ea204eaf349a2c588670a237c9e583b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="port-operations-in-the-net-framework-with-visual-basic"></a>Portové operace v rozhraní .NET Framework s jazykem Visual Basic
Přistupujete k sériovým portům počítače prostřednictvím [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] třídy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů. Nejdůležitější třída <xref:System.IO.Ports.SerialPort>, poskytuje rozhraní pro synchronní a událostmi řízené vstupně-výstupních operací, přístup k PIN kódu a zalomení stavy a přístup k vlastnostem sériového zařízení. Může být uzavřen do <xref:System.IO.Stream> objekt, přístupný prostřednictvím <xref:System.IO.Ports.SerialPort.BaseStream%2A> vlastnost. Zabalení <xref:System.IO.Ports.SerialPort> v <xref:System.IO.Stream> objekt umožňuje sériového portu, ke kterým přistupují třídy, které používají datových proudů. Obor názvů zahrnuje výčty, které zjednodušují ovládacího prvku sériových portů.  
  
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
 [Přístup k portům počítače](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md)
