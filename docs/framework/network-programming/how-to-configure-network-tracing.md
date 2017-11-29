---
title: "Postupy: Konfigurace trasování sítě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "23"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 12f328d58ef568c78d1e2c8a8ff564839cba9f3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-network-tracing"></a>Postupy: Konfigurace trasování sítě
Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Informace o povolení trasování najdete v tématu [povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Konfigurační soubor počítače machine.config je uložen ve složce %Windir%\Microsoft.NET\Framework v adresáři, do něhož byl nainstalován systém Windows. Samostatné machine.config soubor existuje ve složkách v části %Windir%\Microsoft.NET\Framework pro každou verzi rozhraní .NET Framework nainstalované v počítači (například C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config nebo C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
 Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.  
  
### <a name="to-configure-network-tracing"></a>Konfigurace trasování sítě  
  
-   Přidejte následující řádky do příslušného konfiguračního souboru. Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.  
  
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
          />  
        </sharedListeners>  
        <trace autoflush="true"/>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
 Když přidáte název, který `<switches>` bloku výstup trasování obsahuje informace z některé metody, které souvisejí s názvem. Výstup popisuje následující tabulka.  
  
|Název|Výstup z|  
|----------|-----------------|  
|`System.Net.Sockets`|Některé veřejné metody třídy <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, a <xref:System.Net.Dns> třídy|  
|`System.Net`|Některé veřejné metody třídy <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, a <xref:System.Net.FtpWebResponse> třídy a SSL ladicí informace (neplatný certifikáty, chybějící seznam vystavitelů a chyby certifikátu klienta.)|  
|`System.Net.HttpListener`|Některé veřejné metody třídy <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, a <xref:System.Net.HttpListenerResponse> třídy.|  
|`System.Net.Cache`|Některé metody privátní a interní v `System.Net.Cache`.|  
|`System.Net.Http`|Některé veřejné metody třídy <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, a <xref:System.Net.Http.WebRequestHandler> třídy.|  
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody třídy <xref:System.Net.WebSockets.ClientWebSocket> a <xref:System.Net.WebSockets.WebSocket> třídy.|  
  
 Výstup trasování konfigurují atributy uvedené v následující tabulce.  
  
|Název atributu|Hodnota atributu|  
|--------------------|---------------------|  
|`Value`|Požadované <xref:System.String> atribut. Nastavuje úroveň podrobností výstupu. Legitimní hodnoty jsou `Critical`, `Error`, `Verbose`, `Warning`, a `Information`.<br /><br /> Tento atribut musí být nastaven na \<přidat název > elementu \<přepínače > elementu, jak je znázorněno v příkladu. Je vyvolána výjimka, pokud tento atribut nastavený na \<zdroje > elementu.|  
|`maxdatasize`|Volitelné <xref:System.Int32> atribut. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br /> Tento atribut musí být nastaven na \<zdroje > elementu, jak je znázorněno v příkladu. Pokud tento atribut nastaví na element v části, je vyvolána výjimka \<přepínače > elementu.|  
|`Tracemode`|Volitelné <xref:System.String> atribut. Nastavte na `includehex` zobrazíte trasování protokolu ve formátu hexadecimální a text. Nastavte na `protocolonly` zobrazíte pouze text. Výchozí hodnota je `includehex`.<br /><br /> Tento atribut musí být nastaven na \<přepínače > elementu, jak je znázorněno v příkladu. Je vyvolána výjimka, pokud tento atribut nastaví na element v části \<zdroje > elementu.|  
  
## <a name="see-also"></a>Viz také  
 [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Úvod do instrumentace a trasování](http://msdn.microsoft.com/en-us/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
