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
ms.openlocfilehash: 50ad01376f3de9cda26f6b00e2d32fc8d3dabdcd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642747"
---
# <a name="enabling-network-tracing"></a>Povolení trasování sítě
Trasování sítě poskytuje přístup k informacím o vyvoláních metody a přenosech v síti generovaných spravovanou aplikací. Je nutné dokončit následující úlohy, jak povolit trasování sítě ve vaší aplikaci:  
  
- Kompilace kódu s povoleným trasováním. Zobrazit [jak: Podmíněná kompilace pomocí trasování a ladění](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) pro další informace o přepínačích kompilátoru vyžadovaného k povolení trasování.  
  
- Zadejte cíl výstupu trasování.  
  
- Konfigurace chování trasování sítě. Zobrazit [jak: Konfigurace trasování sítě](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) podrobné informace.  
  
 Nejčastěji používané cíle trasování také označuje jako naslouchacími procesy trasování, jsou výchozí naslouchací proces a soubor protokolu.  
  
 Trasování používá výchozí naslouchací proces, pokud nezadáte naslouchací proces trasování. Zobrazí se zprávy odeslané k naslouchacímu procesu výchozí spuštěním kódu v spravovaného ladicího programu s podporou kód například ladicí program CLR, kterou jste dostali se SDK rozhraní .NET Framework, nebo DBwin32.exe součástí sady Windows SDK. Pomocí ladicího programu CLR, trasování zprávy zobrazí ve **výstup** okna.  
  
 Pokud chcete použít soubor pro příjem trasování, můžete zadat soubor protokolu s použitím nastavení konfigurace, jak je znázorněno v následujícím příkladu. (Obecnou diskuzi týkající se konfiguračních souborů, najdete v části [konfigurační soubory](../../../docs/framework/configure-apps/index.md).)  
  
 K odesílání trasování do souboru protokolu, přidejte následující uzel `<system.diagnostics>` uzel příslušného konfiguračního souboru (aplikace nebo počítače). Můžete změnit název souboru (trasování.log) tak, aby odpovídala vašim potřebám.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Viz také:

- [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
- [Trasování a instrumentace aplikací](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
