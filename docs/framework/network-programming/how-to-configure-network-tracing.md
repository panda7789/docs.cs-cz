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
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="594ec-102">Postupy: Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="594ec-102">How to: Configure network tracing</span></span>

<span data-ttu-id="594ec-103">Konfigurační soubor aplikace nebo počítače obsahuje nastavení, která určují formát a obsah trasování sítě.</span><span class="sxs-lookup"><span data-stu-id="594ec-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="594ec-104">Před provedením tohoto postupu zkontrolujte, zda je povoleno trasování.</span><span class="sxs-lookup"><span data-stu-id="594ec-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="594ec-105">Další informace najdete v tématu [Povolení trasování sítě](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="594ec-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="594ec-106">Konfigurační soubor počítače Machine. config je uložený ve složce%windir%\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="594ec-106">The computer configuration file, machine.config, is stored in the %windir%\Microsoft.NET\Framework folder.</span></span> <span data-ttu-id="594ec-107">Pro každou verzi .NET Framework nainstalovanou v počítači existuje samostatný soubor Machine. config ve složkách v rámci%windir%\Microsoft.NET\Framework, například:</span><span class="sxs-lookup"><span data-stu-id="594ec-107">There is a separate machine.config file in the folders under %windir%\Microsoft.NET\Framework for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="594ec-108">C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config</span><span class="sxs-lookup"><span data-stu-id="594ec-108">C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config</span></span>
- <span data-ttu-id="594ec-109">C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config</span><span class="sxs-lookup"><span data-stu-id="594ec-109">C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config</span></span>
  
<span data-ttu-id="594ec-110">Tato nastavení lze provést také v konfiguračním souboru aplikace, který má vyšší prioritu než konfigurační soubor počítače.</span><span class="sxs-lookup"><span data-stu-id="594ec-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>  
  
## <a name="configure-network-tracing"></a><span data-ttu-id="594ec-111">Konfigurace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="594ec-111">Configure network tracing</span></span>  
  
<span data-ttu-id="594ec-112">Chcete-li nakonfigurovat trasování sítě, přidejte následující řádky do příslušného konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="594ec-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="594ec-113">Hodnoty a možnosti těchto nastavení jsou popsány v níže uvedených tabulkách.</span><span class="sxs-lookup"><span data-stu-id="594ec-113">The values and options for these settings are described in the tables below.</span></span>  
  
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

### <a name="trace-output-from-methods"></a><span data-ttu-id="594ec-114">Trasovat výstup z metod</span><span class="sxs-lookup"><span data-stu-id="594ec-114">Trace output from methods</span></span>

<span data-ttu-id="594ec-115">Když přidáte název do bloku `<switches>`, výstup trasování obsahuje informace z některých metod souvisejících s názvem.</span><span class="sxs-lookup"><span data-stu-id="594ec-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="594ec-116">Následující tabulka popisuje výstup:</span><span class="sxs-lookup"><span data-stu-id="594ec-116">The following table describes the output:</span></span>
  
|<span data-ttu-id="594ec-117">Name</span><span class="sxs-lookup"><span data-stu-id="594ec-117">Name</span></span>|<span data-ttu-id="594ec-118">Výstup z</span><span class="sxs-lookup"><span data-stu-id="594ec-118">Output from</span></span>|  
|----------|-----------------|  
|`System.Net.Sockets`|<span data-ttu-id="594ec-119">Některé veřejné metody tříd <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>a <xref:System.Net.Dns>.</span><span class="sxs-lookup"><span data-stu-id="594ec-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|  
|`System.Net`|<span data-ttu-id="594ec-120">Některé veřejné metody tříd <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>a <xref:System.Net.FtpWebResponse> a informace o ladění SSL (neplatné certifikáty, seznam vystavitelů a chyby klientského certifikátu).</span><span class="sxs-lookup"><span data-stu-id="594ec-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|  
|`System.Net.HttpListener`|<span data-ttu-id="594ec-121">Některé veřejné metody tříd <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>a <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="594ec-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|  
|`System.Net.Cache`|<span data-ttu-id="594ec-122">Některé soukromé a interní metody v `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="594ec-122">Some private and internal methods in `System.Net.Cache`.</span></span>|  
|`System.Net.Http`|<span data-ttu-id="594ec-123">Některé veřejné metody <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler>a <xref:System.Net.Http.WebRequestHandler> třídy.</span><span class="sxs-lookup"><span data-stu-id="594ec-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|  
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="594ec-124">Některé veřejné metody <xref:System.Net.WebSockets.ClientWebSocket> a <xref:System.Net.WebSockets.WebSocket> třídy.</span><span class="sxs-lookup"><span data-stu-id="594ec-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|  

### <a name="trace-output-attributes"></a><span data-ttu-id="594ec-125">Trasovat výstupní atributy</span><span class="sxs-lookup"><span data-stu-id="594ec-125">Trace output attributes</span></span>

<span data-ttu-id="594ec-126">Atributy uvedené v následující tabulce konfigurují výstupy trasování:</span><span class="sxs-lookup"><span data-stu-id="594ec-126">The attributes listed in the following table configure trace output:</span></span>
  
|<span data-ttu-id="594ec-127">Název atributu</span><span class="sxs-lookup"><span data-stu-id="594ec-127">Attribute name</span></span>|<span data-ttu-id="594ec-128">Hodnota atributu</span><span class="sxs-lookup"><span data-stu-id="594ec-128">Attribute value</span></span>|  
|--------------------|---------------------|  
|`value`|<span data-ttu-id="594ec-129">Požadovaný atribut <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="594ec-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="594ec-130">Nastavuje úroveň podrobností výstupu.</span><span class="sxs-lookup"><span data-stu-id="594ec-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="594ec-131">Legitimní hodnoty jsou `Critical`, `Error`, `Verbose`, `Warning`a `Information`.</span><span class="sxs-lookup"><span data-stu-id="594ec-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="594ec-132">Tento atribut musí být nastaven na elementu **Add** elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="594ec-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="594ec-133">Pokud je tento atribut nastaven na **zdrojovém** elementu, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="594ec-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="594ec-134">Příklad: `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="594ec-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="594ec-135">Volitelný atribut <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="594ec-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="594ec-136">Nastavuje maximální počet bajtů dat sítě zahrnutých na každém řádku trasování.</span><span class="sxs-lookup"><span data-stu-id="594ec-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="594ec-137">Výchozí hodnota je 1024.</span><span class="sxs-lookup"><span data-stu-id="594ec-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="594ec-138">Tento atribut musí být nastaven u **zdrojového** elementu.</span><span class="sxs-lookup"><span data-stu-id="594ec-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="594ec-139">Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="594ec-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="594ec-140">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="594ec-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="594ec-141">Volitelný atribut <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="594ec-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="594ec-142">Nastavte na `includehex` pro zobrazení trasování protokolu v hexadecimálním a textovém formátu.</span><span class="sxs-lookup"><span data-stu-id="594ec-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="594ec-143">Nastavte na `protocolonly`, aby se zobrazil jenom text.</span><span class="sxs-lookup"><span data-stu-id="594ec-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="594ec-144">Výchozí hodnota je `includehex`.</span><span class="sxs-lookup"><span data-stu-id="594ec-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="594ec-145">Tento atribut musí být nastaven u **zdrojového** elementu.</span><span class="sxs-lookup"><span data-stu-id="594ec-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="594ec-146">Výjimka je vyvolána, pokud je tento atribut nastaven na elementu v rámci elementu **Switched** .</span><span class="sxs-lookup"><span data-stu-id="594ec-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="594ec-147">Příklad: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="594ec-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="594ec-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="594ec-148">See also</span></span>

- [<span data-ttu-id="594ec-149">Interpretace trasování sítě</span><span class="sxs-lookup"><span data-stu-id="594ec-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="594ec-150">Trasování sítě v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="594ec-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="594ec-151">Povolení trasování sítě</span><span class="sxs-lookup"><span data-stu-id="594ec-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="594ec-152">Trasování a instrumentace aplikací</span><span class="sxs-lookup"><span data-stu-id="594ec-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
