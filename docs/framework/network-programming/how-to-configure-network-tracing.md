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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="d46d0-102">Postup: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="d46d0-102">How to: Configure network tracing</span></span>

<span data-ttu-id="d46d0-103">Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě.</span><span class="sxs-lookup"><span data-stu-id="d46d0-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="d46d0-104">Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování.</span><span class="sxs-lookup"><span data-stu-id="d46d0-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="d46d0-105">Další informace naleznete v [tématu Enable network trasování](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="d46d0-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="d46d0-106">Konfigurační soubor počítače *machine.config*je uložen ve složce *%windir%\Microsoft.NET\Framework.*</span><span class="sxs-lookup"><span data-stu-id="d46d0-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="d46d0-107">Ve složkách pod *položkou %windir%\Microsoft.NET\Framework* je samostatný soubor *machine.config* pro každou verzi rozhraní .NET Framework nainstalovanou v počítači, například:</span><span class="sxs-lookup"><span data-stu-id="d46d0-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="d46d0-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="d46d0-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="d46d0-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="d46d0-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="d46d0-110">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="d46d0-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="d46d0-111">Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="d46d0-111">Configure network tracing</span></span>

<span data-ttu-id="d46d0-112">Chcete-li konfigurovat trasování sítě, přidejte do příslušného konfiguračního souboru následující řádky.</span><span class="sxs-lookup"><span data-stu-id="d46d0-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="d46d0-113">Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.</span><span class="sxs-lookup"><span data-stu-id="d46d0-113">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="d46d0-114">Výstup trasování z metod</span><span class="sxs-lookup"><span data-stu-id="d46d0-114">Trace output from methods</span></span>

<span data-ttu-id="d46d0-115">Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s názvem.</span><span class="sxs-lookup"><span data-stu-id="d46d0-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="d46d0-116">Následující tabulka popisuje výstup:</span><span class="sxs-lookup"><span data-stu-id="d46d0-116">The following table describes the output:</span></span>

|<span data-ttu-id="d46d0-117">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="d46d0-117">Name</span></span>|<span data-ttu-id="d46d0-118">Výstup z</span><span class="sxs-lookup"><span data-stu-id="d46d0-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="d46d0-119">Některé veřejné metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Dns> a třídy.</span><span class="sxs-lookup"><span data-stu-id="d46d0-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="d46d0-120">Některé veřejné metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.FtpWebResponse> a třídy a SSL ladicí informace (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu).</span><span class="sxs-lookup"><span data-stu-id="d46d0-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="d46d0-121">Některé veřejné metody <xref:System.Net.HttpListener> <xref:System.Net.HttpListenerRequest>, <xref:System.Net.HttpListenerResponse> a třídy.</span><span class="sxs-lookup"><span data-stu-id="d46d0-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="d46d0-122">Některé soukromé a `System.Net.Cache`interní metody v .</span><span class="sxs-lookup"><span data-stu-id="d46d0-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="d46d0-123">Některé veřejné metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>, <xref:System.Net.Http.WebRequestHandler> , a tříd.</span><span class="sxs-lookup"><span data-stu-id="d46d0-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="d46d0-124">Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> a třídy.</span><span class="sxs-lookup"><span data-stu-id="d46d0-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="d46d0-125">Výstupní atributy trasování</span><span class="sxs-lookup"><span data-stu-id="d46d0-125">Trace output attributes</span></span>

<span data-ttu-id="d46d0-126">Atributy uvedené v následující tabulce nakonfigurují výstup trasování:</span><span class="sxs-lookup"><span data-stu-id="d46d0-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="d46d0-127">Název atributu</span><span class="sxs-lookup"><span data-stu-id="d46d0-127">Attribute name</span></span>|<span data-ttu-id="d46d0-128">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="d46d0-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="d46d0-129">Povinný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="d46d0-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="d46d0-130">Nastavuje úroveň podrobností výstupu.</span><span class="sxs-lookup"><span data-stu-id="d46d0-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="d46d0-131">Legitimní hodnoty `Critical` `Error`jsou `Verbose` `Warning`, `Information`, , a .</span><span class="sxs-lookup"><span data-stu-id="d46d0-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="d46d0-132">Tento atribut musí být nastaven na **elementu add** prvku **switches.**</span><span class="sxs-lookup"><span data-stu-id="d46d0-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="d46d0-133">Výjimka je vyvolána, pokud je tento atribut nastaven na **zdrojový** prvek.</span><span class="sxs-lookup"><span data-stu-id="d46d0-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="d46d0-134">Příklad: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="d46d0-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="d46d0-135">Volitelný <xref:System.Int32> atribut.</span><span class="sxs-lookup"><span data-stu-id="d46d0-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="d46d0-136">Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování.</span><span class="sxs-lookup"><span data-stu-id="d46d0-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="d46d0-137">Výchozí hodnota je 1024.</span><span class="sxs-lookup"><span data-stu-id="d46d0-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="d46d0-138">Tento atribut musí být nastaven na **zdrojový** prvek.</span><span class="sxs-lookup"><span data-stu-id="d46d0-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="d46d0-139">Výjimka je vyvolána, pokud je tento atribut nastaven na prvek pod prvek **přepínače.**</span><span class="sxs-lookup"><span data-stu-id="d46d0-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="d46d0-140">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="d46d0-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="d46d0-141">Volitelný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="d46d0-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="d46d0-142">Nastavte `includehex` na zobrazení trasování protokolu v šestnáctkovém a textovém formátu.</span><span class="sxs-lookup"><span data-stu-id="d46d0-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="d46d0-143">Nastaveno `protocolonly` na zobrazení pouze textu.</span><span class="sxs-lookup"><span data-stu-id="d46d0-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="d46d0-144">Výchozí hodnota je `includehex`.</span><span class="sxs-lookup"><span data-stu-id="d46d0-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="d46d0-145">Tento atribut musí být nastaven na **zdrojový** prvek.</span><span class="sxs-lookup"><span data-stu-id="d46d0-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="d46d0-146">Výjimka je vyvolána, pokud je tento atribut nastaven na prvek pod prvek **přepínače.**</span><span class="sxs-lookup"><span data-stu-id="d46d0-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="d46d0-147">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="d46d0-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="d46d0-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="d46d0-148">See also</span></span>

- [<span data-ttu-id="d46d0-149">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="d46d0-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="d46d0-150">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d46d0-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="d46d0-151">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="d46d0-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="d46d0-152">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="d46d0-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
