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
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048372"
---
# <a name="how-to-configure-network-tracing"></a>Postupy: Konfigurace trasování sítě
Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Informace o povolení trasování najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).  
  
 Konfigurační soubor počítače machine.config je uložen ve složce %Windir%\Microsoft.NET\Framework v adresáři, do něhož byl nainstalován systém Windows. Ve složkách v%Windir%\Microsoft.NET\Framework je k dispozici samostatný soubor Machine. config pro každou verzi .NET Framework nainstalovanou v počítači (například C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config nebo C:\Windows\ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
### <a name="to-configure-network-tracing"></a>Konfigurace trasování sítě  
  
- Přidejte následující řádky do příslušného konfiguračního souboru. Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.  
  
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
  
 Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s tímto názvem. Výstup popisuje následující tabulka.  
  
|Name|Výstup z|  
|----------|-----------------|  
|`System.Net.Sockets`|Některé <xref:System.Net.Sockets.Socket>veřejné metody <xref:System.Net.Sockets.TcpListener> tříd<xref:System.Net.Dns> ,, <xref:System.Net.Sockets.TcpClient>a|  
|`System.Net`|Některé veřejné metody <xref:System.Net.HttpWebRequest>tříd, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>a <xref:System.Net.FtpWebResponse> a ladicí informace SSL (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu)|  
|`System.Net.HttpListener`|Některé veřejné metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerResponse> tříd, <xref:System.Net.HttpListenerRequest>a.|  
|`System.Net.Cache`|Některé soukromé a interní metody v `System.Net.Cache`.|  
|`System.Net.Http`|Některé <xref:System.Net.Http.HttpClient>veřejné metody <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.DelegatingHandler> tříd<xref:System.Net.Http.WebRequestHandler> ,, <xref:System.Net.Http.HttpMessageHandler>, ,<xref:System.Net.Http.MessageProcessingHandler>a.|  
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> tříd a <xref:System.Net.WebSockets.WebSocket> .|  
  
 Výstup trasování konfigurují atributy uvedené v následující tabulce.  
  
|Název atributu|Hodnota atributu|  
|--------------------|---------------------|  
|`Value`|Požadovaný <xref:System.String> atribut. Nastavuje úroveň podrobností výstupu. Legitimní hodnoty jsou `Critical`, `Error`, `Verbose` `Warning`, a .`Information`<br /><br /> Tento atribut musí být nastaven na \<prvku add name > elementu \<Switches > elementu, jak je znázorněno v příkladu. Pokud je tento atribut nastaven na \<zdrojovém > elementu, je vyvolána výjimka.|  
|`maxdatasize`|Volitelný <xref:System.Int32> atribut. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br /> Tento atribut musí být nastaven na \<zdrojovém > element, jak je znázorněno v příkladu. Výjimka je vyvolána, pokud je tento atribut nastaven na prvku pod \<přepínači > elementu.|  
|`Tracemode`|Volitelný <xref:System.String> atribut. `includehex` Nastavte na zobrazovat trasování protokolu v hexadecimálním a textovém formátu. `protocolonly` Nastavte na hodnotu zobrazit pouze text. Výchozí hodnota je `includehex`.<br /><br /> Tento atribut musí být nastaven u \<přepínačů > element, jak je znázorněno v příkladu. Výjimka je vyvolána, pokud je tento atribut nastaven na prvku pod \<zdrojovým > prvkem.|  
  
## <a name="see-also"></a>Viz také:

- [Interpretace trasování sítě](interpreting-network-tracing.md)
- [Trasování sítě v rozhraní .NET Framework](network-tracing.md)
- [Povolení trasování sítě](enabling-network-tracing.md)
- [Trasování a instrumentace aplikací](../debug-trace-profile/tracing-and-instrumenting-applications.md)
