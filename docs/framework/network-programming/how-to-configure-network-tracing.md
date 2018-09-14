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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3c9550bf9d3483a8d2961e6137138bfb11f71bca
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527587"
---
# <a name="how-to-configure-network-tracing"></a>Postupy: Konfigurace trasování sítě
Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě. Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování. Informace o povolení trasování najdete v tématu [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).  
  
 Konfigurační soubor počítače machine.config je uložen ve složce %Windir%\Microsoft.NET\Framework v adresáři, do něhož byl nainstalován systém Windows. Existuje soubor machine.config samostatné do složky ve složce %Windir%\Microsoft.NET\Framework pro každou verzi rozhraní .NET Framework nainstalované v počítači (například C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config nebo C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).  
  
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
  
 Když přidáte název, který `<switches>` bloku, výstup trasování obsahovat informace z některé metody s tímto názvem souvisejí. Výstup popisuje následující tabulka.  
  
|Název|Výstup z|  
|----------|-----------------|  
|`System.Net.Sockets`|Některé veřejné metody <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, a <xref:System.Net.Dns> třídy|  
|`System.Net`|Některé veřejné metody <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, a <xref:System.Net.FtpWebResponse> třídy a ladicí informace (neplatné certifikáty, seznam chybějících vydavatelů a chyby klientských certifikátů.) protokolu SSL|  
|`System.Net.HttpListener`|Některé veřejné metody <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, a <xref:System.Net.HttpListenerResponse> třídy.|  
|`System.Net.Cache`|Některé soukromé a vnitřní metody v `System.Net.Cache`.|  
|`System.Net.Http`|Některé veřejné metody <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, a <xref:System.Net.Http.WebRequestHandler> třídy.|  
|`System.Net.WebSockets.WebSocket`|Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> a <xref:System.Net.WebSockets.WebSocket> třídy.|  
  
 Výstup trasování konfigurují atributy uvedené v následující tabulce.  
  
|Název atributu|Hodnota atributu|  
|--------------------|---------------------|  
|`Value`|Vyžaduje <xref:System.String> atribut. Nastavuje úroveň podrobností výstupu. Platné hodnoty jsou `Critical`, `Error`, `Verbose`, `Warning`, a `Information`.<br /><br /> Tento atribut musí být nastaven na \<přidejte název > element \<přepínače > element, jak je znázorněno v příkladu. Výjimka je vyvolána, pokud tento atribut je nastaven na \<zdroj > element.|  
|`maxdatasize`|Volitelné <xref:System.Int32> atribut. Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování. Výchozí hodnota je 1024.<br /><br /> Tento atribut musí být nastaven na \<zdroj > element, jak je znázorněno v příkladu. Výjimka je vyvolána, pokud tento atribut je nastaven pro element v rámci \<přepínače > element.|  
|`Tracemode`|Volitelné <xref:System.String> atribut. Nastavte na `includehex` chcete protokol trasování zobrazit v šestnáctkovém a textovém formátu. Nastavte na `protocolonly` chcete zobrazit pouze text. Výchozí hodnota je `includehex`.<br /><br /> Tento atribut musí být nastaven na \<přepínače > element, jak je znázorněno v příkladu. Výjimka je vyvolána, pokud tento atribut je nastaven pro element v rámci \<zdroj > element.|  
  
## <a name="see-also"></a>Viz také  
 [Interpretace trasování sítě](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Trasování sítě v rozhraní .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Povolení trasování sítě](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Úvod do trasování a instrumentace](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
