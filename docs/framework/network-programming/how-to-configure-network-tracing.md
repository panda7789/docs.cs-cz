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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="2b889-102">Postupy: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="2b889-102">How to: Configure Network Tracing</span></span>
<span data-ttu-id="2b889-103">Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě.</span><span class="sxs-lookup"><span data-stu-id="2b889-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="2b889-104">Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování.</span><span class="sxs-lookup"><span data-stu-id="2b889-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="2b889-105">Informace o povolení trasování najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="2b889-105">For information about enabling tracing, see [Enabling Network Tracing](enabling-network-tracing.md).</span></span>  
  
 <span data-ttu-id="2b889-106">Konfigurační soubor počítače machine.config je uložen ve složce %Windir%\Microsoft.NET\Framework v adresáři, do něhož byl nainstalován systém Windows.</span><span class="sxs-lookup"><span data-stu-id="2b889-106">The computer configuration file, machine.config, is stored in the %Windir%\Microsoft.NET\Framework folder in the directory where Windows was installed.</span></span> <span data-ttu-id="2b889-107">Ve složkách v%Windir%\Microsoft.NET\Framework je k dispozici samostatný soubor Machine. config pro každou verzi .NET Framework nainstalovanou v počítači (například C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config nebo C:\Windows\ Microsoft. NET\Framework64\v4.0.30319\Config\machine.config.).</span><span class="sxs-lookup"><span data-stu-id="2b889-107">There is a separate machine.config file in the folders under %Windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer (for example, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config or C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config.).</span></span>  
  
 <span data-ttu-id="2b889-108">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="2b889-108">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
### <a name="to-configure-network-tracing"></a><span data-ttu-id="2b889-109">Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="2b889-109">To configure network tracing</span></span>  
  
- <span data-ttu-id="2b889-110">Přidejte následující řádky do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2b889-110">Add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="2b889-111">Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.</span><span class="sxs-lookup"><span data-stu-id="2b889-111">The values and options for these settings are described in the tables below.</span></span>  
  
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
  
 <span data-ttu-id="2b889-112">Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="2b889-112">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="2b889-113">Výstup popisuje následující tabulka.</span><span class="sxs-lookup"><span data-stu-id="2b889-113">The following table describes the output.</span></span>  
  
|<span data-ttu-id="2b889-114">Name</span><span class="sxs-lookup"><span data-stu-id="2b889-114">Name</span></span>|<span data-ttu-id="2b889-115">Výstup z</span><span class="sxs-lookup"><span data-stu-id="2b889-115">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="2b889-116">Některé <xref:System.Net.Sockets.Socket>veřejné metody <xref:System.Net.Sockets.TcpListener> tříd<xref:System.Net.Dns> ,, <xref:System.Net.Sockets.TcpClient>a</span><span class="sxs-lookup"><span data-stu-id="2b889-116">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes</span></span>|  
|`System.Net`|<span data-ttu-id="2b889-117">Některé veřejné metody <xref:System.Net.HttpWebRequest>tříd, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>a <xref:System.Net.FtpWebResponse> a ladicí informace SSL (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu)</span><span class="sxs-lookup"><span data-stu-id="2b889-117">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors.)</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="2b889-118">Některé veřejné metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerResponse> tříd, <xref:System.Net.HttpListenerRequest>a.</span><span class="sxs-lookup"><span data-stu-id="2b889-118">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="2b889-119">Některé soukromé a interní metody v `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="2b889-119">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="2b889-120">Některé <xref:System.Net.Http.HttpClient>veřejné metody <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.DelegatingHandler> tříd<xref:System.Net.Http.WebRequestHandler> ,, <xref:System.Net.Http.HttpMessageHandler>, ,<xref:System.Net.Http.MessageProcessingHandler>a.</span><span class="sxs-lookup"><span data-stu-id="2b889-120">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="2b889-121">Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> tříd a <xref:System.Net.WebSockets.WebSocket> .</span><span class="sxs-lookup"><span data-stu-id="2b889-121">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  
  
 <span data-ttu-id="2b889-122">Výstup trasování konfigurují atributy uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2b889-122">The attributes listed in the following table configure trace output.</span></span>  
  
|<span data-ttu-id="2b889-123">Název atributu</span><span class="sxs-lookup"><span data-stu-id="2b889-123">Attribute name</span></span>|<span data-ttu-id="2b889-124">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="2b889-124">Attribute value</span></span>|  
|--------------------|---------------------|  
|`Value`|<span data-ttu-id="2b889-125">Požadovaný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="2b889-125">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="2b889-126">Nastavuje úroveň podrobností výstupu.</span><span class="sxs-lookup"><span data-stu-id="2b889-126">Sets the verbosity of the output.</span></span> <span data-ttu-id="2b889-127">Legitimní hodnoty jsou `Critical`, `Error`, `Verbose` `Warning`, a .`Information`</span><span class="sxs-lookup"><span data-stu-id="2b889-127">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /> <span data-ttu-id="2b889-128">Tento atribut musí být nastaven na \<prvku add name > elementu \<Switches > elementu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b889-128">This attribute must be set on the \<add name> element of the \<switches> element as shown in the example.</span></span> <span data-ttu-id="2b889-129">Pokud je tento atribut nastaven na \<zdrojovém > elementu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2b889-129">An exception is thrown if this attribute is set on the \<source> element.</span></span>|  
|`maxdatasize`|<span data-ttu-id="2b889-130">Volitelný <xref:System.Int32> atribut.</span><span class="sxs-lookup"><span data-stu-id="2b889-130">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="2b889-131">Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování.</span><span class="sxs-lookup"><span data-stu-id="2b889-131">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="2b889-132">Výchozí hodnota je 1024.</span><span class="sxs-lookup"><span data-stu-id="2b889-132">The default value is 1024.</span></span><br /><br /> <span data-ttu-id="2b889-133">Tento atribut musí být nastaven na \<zdrojovém > element, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b889-133">This attribute must be set on the \<source> element as shown in the example.</span></span> <span data-ttu-id="2b889-134">Výjimka je vyvolána, pokud je tento atribut nastaven na prvku pod \<přepínači > elementu.</span><span class="sxs-lookup"><span data-stu-id="2b889-134">An exception is thrown if this attribute is set on an element under the \<switches> element.</span></span>|  
|`Tracemode`|<span data-ttu-id="2b889-135">Volitelný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="2b889-135">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="2b889-136">`includehex` Nastavte na zobrazovat trasování protokolu v hexadecimálním a textovém formátu.</span><span class="sxs-lookup"><span data-stu-id="2b889-136">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="2b889-137">`protocolonly` Nastavte na hodnotu zobrazit pouze text.</span><span class="sxs-lookup"><span data-stu-id="2b889-137">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="2b889-138">Výchozí hodnota je `includehex`.</span><span class="sxs-lookup"><span data-stu-id="2b889-138">The default value is `includehex`.</span></span><br /><br /> <span data-ttu-id="2b889-139">Tento atribut musí být nastaven u \<přepínačů > element, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="2b889-139">This attribute must be set on the \<switches> element as shown in the example.</span></span> <span data-ttu-id="2b889-140">Výjimka je vyvolána, pokud je tento atribut nastaven na prvku pod \<zdrojovým > prvkem.</span><span class="sxs-lookup"><span data-stu-id="2b889-140">An exception is thrown if this attribute is set on an element under the \<source> element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b889-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b889-141">See also</span></span>

- [<span data-ttu-id="2b889-142">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="2b889-142">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="2b889-143">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2b889-143">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="2b889-144">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="2b889-144">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="2b889-145">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="2b889-145">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
