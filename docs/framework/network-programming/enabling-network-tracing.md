---
title: Povolení trasování sítě
description: Naučte se, jak povolit trasování sítě, které poskytuje informace o vyvoláních metod a síťovém provozu pro spravovanou aplikaci v .NET Framework.
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
ms.openlocfilehash: 4ad0b23fc93ddcdc11cebcc556d12148df5e8ae2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502597"
---
# <a name="enabling-network-tracing"></a>Povolení trasování sítě
Trasování sítě poskytuje přístup k informacím o vyvoláních metod a síťovém provozu vygenerovaném spravovanou aplikací. Chcete-li povolit trasování sítě v aplikaci, je nutné provést následující úlohy:  
  
- Zkompilujte kód s povoleným trasováním. Další informace o přepínačích kompilátoru vyžadovaných k povolení trasování naleznete v tématu [How to: Conditioning with Trace and Debug](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) .  
  
- Zadejte cíl pro trasování výstupu.  
  
- Nakonfigurujte chování trasování sítě. Podrobné informace najdete v tématu [Postup: Konfigurace trasování sítě](how-to-configure-network-tracing.md) .  
  
 Nejběžnějšími cíli trasování, označovaných také jako naslouchací procesy trasování, jsou výchozí naslouchací proces a soubor protokolu.  
  
 Trasování používá výchozí naslouchací proces, pokud nezadáte naslouchací proces trasování. Zprávy odeslané do výchozího naslouchacího procesu můžete zobrazit spuštěním kódu v ladicím programu s povoleným kódem, jako je například ladicí program CLR dodávaný s .NET Framework SDK nebo DBwin32. exe dodaný s Windows SDK. Pomocí ladicího programu CLR se zprávy trasování zobrazí v okně **výstup** .  
  
 Pokud dáváte přednost použití souboru pro příjem trasování, můžete určit soubor protokolu pomocí nastavení konfigurace, jak je znázorněno v následujícím příkladu. (Obecné informace o konfiguračních souborech najdete v tématu [konfigurační soubory](../configure-apps/index.md).)  
  
 Chcete-li odeslat trasování do souboru protokolu, přidejte následující uzel do `<system.diagnostics>` uzlu příslušného konfiguračního souboru (aplikace nebo počítač). Název souboru (Trace. log) můžete změnit tak, aby vyhovoval vašim potřebám.  
  
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

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
