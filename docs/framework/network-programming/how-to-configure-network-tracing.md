---
title: 'Postupy: Konfigurace trasování sítě'
description: Přečtěte si, jak nakonfigurovat trasování sítě v konfiguračním souboru počítače nebo konfiguračního souboru aplikace. Konfigurační soubor aplikace má přednost.
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
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502558"
---
# <a name="how-to-configure-network-tracing"></a>Postupy: Konfigurace trasování sítě

Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Další informace najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).

Konfigurační soubor počítače *Machine. config*je uložený ve složce *%windir%\Microsoft.NET\Framework* . Pro každou verzi .NET Framework nainstalovanou v počítači existuje samostatný soubor *Machine. config* ve složkách v rámci *%windir%\Microsoft.NET\Framework* , například:

- *C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*
- *C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*

Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.

## <a name="configure-network-tracing"></a>Konfigurace trasování sítě

Chcete-li nakonfigurovat trasování sítě, přidejte následující řádky do příslušného konfiguračního souboru. Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.

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

### <a name="trace-output-from-methods"></a>Trasovat výstup z metod

Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s tímto názvem. Následující tabulka popisuje výstup:

|Name|Výstup z|
|----------|-----------------|
|`System.Net.Sockets`|Některé veřejné metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener> tříd,, a <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Dns> .|
|`System.Net`|Některé veřejné metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> tříd,, <xref:System.Net.FtpWebRequest> a a <xref:System.Net.FtpWebResponse> ladicí informace SSL (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu).|
|`System.Net.HttpListener`|Některé veřejné metody <xref:System.Net.HttpListener> tříd, a <xref:System.Net.HttpListenerRequest> <xref:System.Net.HttpListenerResponse> .|
|`System.Net.Cache`|Některé soukromé a interní metody v `System.Net.Cache` .|
|`System.Net.Http`|Některé veřejné metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler> tříd,,, <xref:System.Net.Http.HttpClientHandler> , <xref:System.Net.Http.HttpMessageHandler> a <xref:System.Net.Http.MessageProcessingHandler> <xref:System.Net.Http.WebRequestHandler> .|
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> tříd a.|

### <a name="trace-output-attributes"></a>Trasovat výstupní atributy

Atributy uvedené v následující tabulce konfigurují výstupy trasování:

|Název atributu|Hodnota atributu|
|--------------------|---------------------|
|`value`|Požadovaný <xref:System.String> atribut. Nastavuje úroveň podrobností výstupu. Legitimní hodnoty jsou `Critical` , `Error` ,, a `Verbose` `Warning` `Information` .<br /><br />Tento atribut musí být nastaven na elementu **Add** elementu **Switched** . Pokud je tento atribut nastaven na **zdrojovém** elementu, je vyvolána výjimka.<br/><br/>Příklad: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Volitelný <xref:System.Int32> atribut. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br />Tento atribut musí být nastaven u **zdrojového** elementu. Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Volitelný <xref:System.String> atribut. Nastavte na `includehex` zobrazovat trasování protokolu v hexadecimálním a textovém formátu. Nastavte na hodnotu `protocolonly` Zobrazit pouze text. Výchozí hodnota je `includehex`.<br /><br />Tento atribut musí být nastaven u **zdrojového** elementu. Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Viz také:

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Povolení trasování sítě](enabling-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
