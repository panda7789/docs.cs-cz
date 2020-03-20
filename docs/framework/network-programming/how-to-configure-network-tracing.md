---
title: 'Postupy: Konfigurace trasování sítě'
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040647"
---
# <a name="how-to-configure-network-tracing"></a>Postup: Konfigurace trasování sítě

Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Další informace naleznete v [tématu Enable network trasování](enabling-network-tracing.md).

Konfigurační soubor počítače *machine.config*je uložen ve složce *%windir%\Microsoft.NET\Framework.* Ve složkách pod *položkou %windir%\Microsoft.NET\Framework* je samostatný soubor *machine.config* pro každou verzi rozhraní .NET Framework nainstalovanou v počítači, například:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.

## <a name="configure-network-tracing"></a>Konfigurace trasování sítě

Chcete-li konfigurovat trasování sítě, přidejte do příslušného konfiguračního souboru následující řádky. Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a>Výstup trasování z metod

Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s názvem. Následující tabulka popisuje výstup:

|Name (Název)|Výstup z|
|----------|-----------------|
|`System.Net.Sockets`|Některé veřejné metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Dns> a třídy.|
|`System.Net`|Některé veřejné metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.FtpWebResponse> a třídy a SSL ladicí informace (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu).|
|`System.Net.HttpListener`|Některé veřejné metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest>, <xref:System.Net.HttpListenerResponse> a třídy.|
|`System.Net.Cache`|Některé soukromé a `System.Net.Cache`interní metody v .|
|`System.Net.Http`|Některé veřejné metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, <xref:System.Net.Http.WebRequestHandler> , a tříd.|
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> a třídy.|

### <a name="trace-output-attributes"></a>Výstupní atributy trasování

Atributy uvedené v následující tabulce nakonfigurují výstup trasování:

|Název atributu|Hodnota atributu|
|--------------------|---------------------|
|`value`|Povinný <xref:System.String> atribut. Nastavuje úroveň podrobností výstupu. Legitimní hodnoty `Critical` `Error`jsou `Verbose` `Warning`, `Information`, , a .<br /><br />Tento atribut musí být nastaven na **elementu add** prvku **switches.** Výjimka je vyvolána, pokud je tento atribut nastaven na **zdrojový** prvek.<br/><br/>Příklad: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Volitelný <xref:System.Int32> atribut. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br />Tento atribut musí být nastaven na **zdrojový** prvek. Výjimka je vyvolána, pokud je tento atribut nastaven na prvek pod prvek **přepínače.**<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Volitelný <xref:System.String> atribut. Nastavte `includehex` na zobrazení trasování protokolu v šestnáctkovém a textovém formátu. Nastaveno `protocolonly` na zobrazení pouze textu. Výchozí hodnota je `includehex`.<br /><br />Tento atribut musí být nastaven na **zdrojový** prvek. Výjimka je vyvolána, pokud je tento atribut nastaven na prvek pod prvek **přepínače.**<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Viz také

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Povolení trasování sítě](enabling-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
