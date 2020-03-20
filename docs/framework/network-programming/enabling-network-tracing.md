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
ms.openlocfilehash: 61ffd422463ca70cc34c39dd216ce8e660809dcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180885"
---
# <a name="enabling-network-tracing"></a>Povolení trasování sítě
Trasování sítě poskytuje přístup k informacím o vyvolání metody a síťovém provozu generovaném spravovanou aplikací. Chcete-li v aplikaci povolit trasování sítě, je nutné provést následující úkoly:  
  
- Zkompilujte kód s povoleným trasováním. Další informace o přepínačích kompilátoru, které jsou nutné k povolení trasování, naleznete v [tématu Postup: Podmíněně kompilovat pomocí trasování a ladění.](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
  
- Zadejte cíl pro vektorizaci výstupu.  
  
- Nakonfigurujte chování trasování sítě. Podrobné informace naleznete [v tématu Postup: Konfigurace trasování sítě.](how-to-configure-network-tracing.md)  
  
 Nejběžnější trasovací cíle, označované také jako naslouchací procesy trasování, jsou výchozí naslouchací proces a soubor protokolu.  
  
 Trasování používá výchozí naslouchací proces, pokud nezadáte naslouchací proces trasování. Zprávy odeslané výchozímu naslouchacímu procesu můžete zobrazit spuštěním kódu ve ladicím programu s povoleným spravovaným kódem, například v ladicím programu CLR dodávaného se sadou .NET Framework SDK nebo DBwin32.exe dodávaným se sadou Windows SDK. Pomocí ladicího programu CLR se trasovací zprávy zobrazí v okně **Výstup.**  
  
 Pokud dáváte přednost použití souboru pro příjem trasování, můžete zadat soubor protokolu pomocí nastavení konfigurace, jak je znázorněno v následujícím příkladu. (Obecné diskusní informace o konfiguračních souborech naleznete v [tématu Configuration Files](../configure-apps/index.md).)  
  
 Chcete-li odeslat trasování do souboru protokolu, přidejte následující uzel do `<system.diagnostics>` uzlu příslušného konfiguračního souboru (aplikace nebo počítače). Název souboru (trace.log) můžete změnit tak, aby vyhovoval vašim potřebám.  
  
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

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
