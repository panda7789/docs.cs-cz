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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404324"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="6020e-102">Postupy: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="6020e-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="6020e-103">Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě.</span><span class="sxs-lookup"><span data-stu-id="6020e-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="6020e-104">Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování.</span><span class="sxs-lookup"><span data-stu-id="6020e-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="6020e-105">Informace o povolení trasování najdete v tématu [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="6020e-105">For information about enabling tracing, see [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="6020e-106">Konfigurační soubor počítače machine.config je uložen ve složce %Windir%\Microsoft.NET\Framework v adresáři, do něhož byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="6020e-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="6020e-107">Existuje soubor machine.config samostatné do složky ve složce %Windir%\Microsoft.NET\Framework pro každou verzi rozhraní .NET Framework nainstalované v počítači (například C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config nebo C:\Windows\ Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="6020e-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="6020e-108">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="6020e-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="6020e-109">Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="6020e-109">To configure network tracing</span></span>  
  
-   <span data-ttu-id="6020e-110">Přidejte následující řádky do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6020e-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="6020e-111">Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.</span><span class="sxs-lookup"><span data-stu-id="6020e-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="6020e-112">Když přidáte název, který `<switches>` bloku, výstup trasování obsahovat informace z některé metody s tímto názvem souvisejí.</span><span class="sxs-lookup"><span data-stu-id="6020e-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="6020e-113">Výstup popisuje následující tabulka.</span><span class="sxs-lookup"><span data-stu-id="6020e-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="6020e-114">Název</span><span class="sxs-lookup"><span data-stu-id="6020e-114">Name</span></span>|<span data-ttu-id="6020e-115">Výstup z</span><span class="sxs-lookup"><span data-stu-id="6020e-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="6020e-116">Některé veřejné metody <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, a <xref:System.Net.Dns> třídy</span><span class="sxs-lookup"><span data-stu-id="6020e-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="6020e-117">Některé veřejné metody <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, a <xref:System.Net.FtpWebResponse> třídy a ladicí informace (neplatné certifikáty, seznam chybějících vydavatelů a chyby klientských certifikátů.) protokolu SSL</span><span class="sxs-lookup"><span data-stu-id="6020e-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="6020e-118">Některé veřejné metody <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, a <xref:System.Net.HttpListenerResponse> třídy.</span><span class="sxs-lookup"><span data-stu-id="6020e-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="6020e-119">Některé soukromé a vnitřní metody v `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="6020e-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="6020e-120">Některé veřejné metody <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, a <xref:System.Net.Http.WebRequestHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="6020e-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="6020e-121">Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> a <xref:System.Net.WebSockets.WebSocket> třídy.</span><span class="sxs-lookup"><span data-stu-id="6020e-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="6020e-122">Výstup trasování konfigurují atributy uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="6020e-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="6020e-123">Název atributu</span><span class="sxs-lookup"><span data-stu-id="6020e-123">Attribute name</span></span>|<span data-ttu-id="6020e-124">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="6020e-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="6020e-125">Vyžaduje <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="6020e-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="6020e-126">Nastavuje úroveň podrobností výstupu.</span><span class="sxs-lookup"><span data-stu-id="6020e-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="6020e-127">Platné hodnoty jsou `Critical`, `Error`, `Verbose`, `Warning`, a `Information`.</span><span class="sxs-lookup"><span data-stu-id="6020e-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="6020e-128">Tento atribut musí být nastaven na \<přidejte název > element \<přepínače > element, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="6020e-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="6020e-129">Výjimka je vyvolána, pokud tento atribut je nastaven na \<zdroj > element.</span><span class="sxs-lookup"><span data-stu-id="6020e-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="6020e-130">Volitelné <xref:System.Int32> atribut.</span><span class="sxs-lookup"><span data-stu-id="6020e-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="6020e-131">Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování.</span><span class="sxs-lookup"><span data-stu-id="6020e-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="6020e-132">Výchozí hodnota je 1024.</span><span class="sxs-lookup"><span data-stu-id="6020e-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="6020e-133">Tento atribut musí být nastaven na \<zdroj > element, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="6020e-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="6020e-134">Výjimka je vyvolána, pokud tento atribut je nastaven pro element v rámci \<přepínače > element.</span><span class="sxs-lookup"><span data-stu-id="6020e-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="6020e-135">Volitelné <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="6020e-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="6020e-136">Nastavte na `includehex` chcete protokol trasování zobrazit v šestnáctkovém a textovém formátu.</span><span class="sxs-lookup"><span data-stu-id="6020e-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="6020e-137">Nastavte na `protocolonly` chcete zobrazit pouze text.</span><span class="sxs-lookup"><span data-stu-id="6020e-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="6020e-138">Výchozí hodnota je `includehex`.</span><span class="sxs-lookup"><span data-stu-id="6020e-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="6020e-139">Tento atribut musí být nastaven na \<přepínače > element, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="6020e-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="6020e-140">Výjimka je vyvolána, pokud tento atribut je nastaven pro element v rámci \<zdroj > element.</span><span class="sxs-lookup"><span data-stu-id="6020e-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6020e-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="6020e-141">See Also</span></span>  
 [<span data-ttu-id="6020e-142">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="6020e-142">Interpreting Network Tracing</span></span>](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [<span data-ttu-id="6020e-143">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6020e-143">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 [<span data-ttu-id="6020e-144">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="6020e-144">Enabling Network Tracing</span></span>](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [<span data-ttu-id="6020e-145">Úvod do trasování a instrumentace</span><span class="sxs-lookup"><span data-stu-id="6020e-145">Introduction to Instrumentation and Tracing</span></span>](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
