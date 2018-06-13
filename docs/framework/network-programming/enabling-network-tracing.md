---
title: Povolení trasování sítě
ms.date: 03/30/2017
helpviewer_keywords:
- trace destinations
- sending traces to log file
- trace listeners, network tracing
- network tracing, enabling
- CLR Debugger
- default listeners
- logs, trace
- destination for tracing output
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56a24f93e92fbfbd2dbb1156a1c3ef786f59034e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390458"
---
# <a name="enabling-network-tracing"></a>Povolení trasování sítě
Trasování sítě poskytuje přístup k informacím o volání metod a síťových přenosů generovaných spravované aplikace. Musíte provést následující úkoly a povolit trasování sítě ve vaší aplikaci:  
  
-   Kompilace kódu s povolené trasování. V tématu [postupy: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) Další informace o přepínače kompilátoru vyžadovaného k povolení trasování.  
  
-   Určete cíl pro výstup trasování.  
  
-   Konfigurace chování trasování sítě. V tématu [postupy: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) podrobné informace.  
  
 Nejběžnější trasování cíle, také označuje jako trasování – moduly naslouchání, jsou výchozí naslouchací proces a soubor protokolu.  
  
 Trasování používá výchozí naslouchací proces, pokud nezadáte naslouchací proces trasování. Můžete zobrazit zprávy odeslané do výchozí naslouchací proces spuštěním kódu v spravované ladicí program povolená kód, jako je součástí ladicí program CLR rozhraní .NET Framework SDK nebo DBwin32.exe součástí sady Windows SDK. Pomocí ladicí program CLR, trasovací zprávy se zobrazují v **výstup** okno.  
  
 Pokud byste radši chtěli použít soubor pro příjem trasování, můžete soubor protokolu pomocí nastavení konfigurace, jak je znázorněno v následujícím příkladu. (Obecná diskuse konfigurační soubory, najdete v části [konfigurační soubory](../../../docs/framework/configure-apps/index.md).)  
  
 K odeslání do souboru protokolu trasování, přidejte následující uzel `<system.diagnostics>` uzlu odpovídající konfigurační soubor (aplikace nebo počítače). Můžete změnit název souboru (trasování.log) tak, aby vyhovovala vašim potřebám.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Viz také  
 [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Úvod do instrumentace a trasování](http://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
