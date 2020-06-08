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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="a8c0b-104">Postupy: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="a8c0b-104">How to: Configure network tracing</span></span>

<span data-ttu-id="a8c0b-105">Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="a8c0b-106">Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="a8c0b-107">Další informace najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="a8c0b-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="a8c0b-108">Konfigurační soubor počítače *Machine. config*je uložený ve složce *%windir%\Microsoft.NET\Framework* .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="a8c0b-109">Pro každou verzi .NET Framework nainstalovanou v počítači existuje samostatný soubor *Machine. config* ve složkách v rámci *%windir%\Microsoft.NET\Framework* , například:</span><span class="sxs-lookup"><span data-stu-id="a8c0b-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="a8c0b-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="a8c0b-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="a8c0b-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="a8c0b-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="a8c0b-112">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="a8c0b-113">Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="a8c0b-113">Configure network tracing</span></span>

<span data-ttu-id="a8c0b-114">Chcete-li nakonfigurovat trasování sítě, přidejte následující řádky do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="a8c0b-115">Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-115">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="a8c0b-116">Trasovat výstup z metod</span><span class="sxs-lookup"><span data-stu-id="a8c0b-116">Trace output from methods</span></span>

<span data-ttu-id="a8c0b-117">Když přidáte název do `<switches>` bloku, výstup trasování obsahuje informace z některých metod souvisejících s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="a8c0b-118">Následující tabulka popisuje výstup:</span><span class="sxs-lookup"><span data-stu-id="a8c0b-118">The following table describes the output:</span></span>

|<span data-ttu-id="a8c0b-119">Name</span><span class="sxs-lookup"><span data-stu-id="a8c0b-119">Name</span></span>|<span data-ttu-id="a8c0b-120">Výstup z</span><span class="sxs-lookup"><span data-stu-id="a8c0b-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="a8c0b-121">Některé veřejné metody <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener> tříd,, a <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="a8c0b-122">Některé veřejné metody <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse> tříd,, <xref:System.Net.FtpWebRequest> a a <xref:System.Net.FtpWebResponse> ladicí informace SSL (neplatné certifikáty, chybějící seznam vystavitelů a chyby klientského certifikátu).</span><span class="sxs-lookup"><span data-stu-id="a8c0b-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="a8c0b-123">Některé veřejné metody <xref:System.Net.HttpListener> tříd, a <xref:System.Net.HttpListenerRequest> <xref:System.Net.HttpListenerResponse> .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="a8c0b-124">Některé soukromé a interní metody v `System.Net.Cache` .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="a8c0b-125">Některé veřejné metody <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.DelegatingHandler> tříd,,, <xref:System.Net.Http.HttpClientHandler> , <xref:System.Net.Http.HttpMessageHandler> a <xref:System.Net.Http.MessageProcessingHandler> <xref:System.Net.Http.WebRequestHandler> .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="a8c0b-126">Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> <xref:System.Net.WebSockets.WebSocket> tříd a.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="a8c0b-127">Trasovat výstupní atributy</span><span class="sxs-lookup"><span data-stu-id="a8c0b-127">Trace output attributes</span></span>

<span data-ttu-id="a8c0b-128">Atributy uvedené v následující tabulce konfigurují výstupy trasování:</span><span class="sxs-lookup"><span data-stu-id="a8c0b-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="a8c0b-129">Název atributu</span><span class="sxs-lookup"><span data-stu-id="a8c0b-129">Attribute name</span></span>|<span data-ttu-id="a8c0b-130">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="a8c0b-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="a8c0b-131">Požadovaný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="a8c0b-132">Nastavuje úroveň podrobností výstupu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="a8c0b-133">Legitimní hodnoty jsou `Critical` , `Error` ,, a `Verbose` `Warning` `Information` .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="a8c0b-134">Tento atribut musí být nastaven na elementu **Add** elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="a8c0b-135">Pokud je tento atribut nastaven na **zdrojovém** elementu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="a8c0b-136">Příklad: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="a8c0b-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="a8c0b-137">Volitelný <xref:System.Int32> atribut.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="a8c0b-138">Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="a8c0b-139">Výchozí hodnota je 1024.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="a8c0b-140">Tento atribut musí být nastaven u **zdrojového** elementu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="a8c0b-141">Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="a8c0b-142">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="a8c0b-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="a8c0b-143">Volitelný <xref:System.String> atribut.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="a8c0b-144">Nastavte na `includehex` zobrazovat trasování protokolu v hexadecimálním a textovém formátu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="a8c0b-145">Nastavte na hodnotu `protocolonly` Zobrazit pouze text.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="a8c0b-146">Výchozí hodnota je `includehex`.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="a8c0b-147">Tento atribut musí být nastaven u **zdrojového** elementu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="a8c0b-148">Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="a8c0b-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="a8c0b-149">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="a8c0b-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="a8c0b-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8c0b-150">See also</span></span>

- [<span data-ttu-id="a8c0b-151">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="a8c0b-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="a8c0b-152">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a8c0b-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="a8c0b-153">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="a8c0b-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="a8c0b-154">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="a8c0b-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
