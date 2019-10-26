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
ms.openlocfilehash: 98854fa0dff8d4cfb1d67d5864751ab01a21150b
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920300"
---
# <a name="how-to-configure-network-tracing"></a>Postupy: Konfigurace trasování sítě

Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Další informace najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).

Konfigurační soubor počítače Machine. config je uložený ve složce%windir%\Microsoft.NET\Framework. Pro každou verzi .NET Framework nainstalovanou v počítači existuje samostatný soubor Machine. config ve složkách v rámci%windir%\Microsoft.NET\Framework, například:

- C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config
- C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config
  
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

Když přidáte název do bloku `<switches>`, výstup trasování obsahuje informace z některých metod souvisejících s názvem. Následující tabulka popisuje výstup:
  
|Name|Výstup z|  
|----------|-----------------|  
|`System.Net.Sockets`|Některé veřejné metody tříd <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>a <xref:System.Net.Dns>.|  
|`System.Net`|Některé veřejné metody tříd <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>a <xref:System.Net.FtpWebResponse> a informace o ladění SSL (neplatné certifikáty, seznam vystavitelů a chyby klientského certifikátu).|  
|`System.Net.HttpListener`|Některé veřejné metody tříd <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>a <xref:System.Net.HttpListenerResponse>.|  
|`System.Net.Cache`|Některé soukromé a interní metody v `System.Net.Cache`.|  
|`System.Net.Http`|Některé veřejné metody <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>a <xref:System.Net.Http.WebRequestHandler> třídy.|  
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> a <xref:System.Net.WebSockets.WebSocket> třídy.|  

### <a name="trace-output-attributes"></a>Trasovat výstupní atributy

Atributy uvedené v následující tabulce konfigurují výstupy trasování:
  
|Název atributu|Hodnota atributu|  
|--------------------|---------------------|  
|`value`|Požadovaný atribut <xref:System.String>. Nastavuje úroveň podrobností výstupu. Legitimní hodnoty jsou `Critical`, `Error`, `Verbose`, `Warning`a `Information`.<br /><br />Tento atribut musí být nastaven na elementu **Add** elementu **Switched** . Pokud je tento atribut nastaven na **zdrojovém** elementu, je vyvolána výjimka.<br/><br/>Příklad: `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Volitelný atribut <xref:System.Int32>. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br />Tento atribut musí být nastaven u **zdrojového** elementu. Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Volitelný atribut <xref:System.String>. Nastavte na `includehex` pro zobrazení trasování protokolu v hexadecimálním a textovém formátu. Nastavte na `protocolonly`, aby se zobrazil jenom text. Výchozí hodnota je `includehex`.<br /><br />Tento atribut musí být nastaven u **zdrojového** elementu. Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .<br/><br/>Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
  
## <a name="see-also"></a>Viz také:

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Povolení trasování sítě](enabling-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
