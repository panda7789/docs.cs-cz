---
title: "&lt;httpListener&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 14a758f1d69da4db8ed58809de20d3522ea7e4e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lthttplistenergt-element-network-settings"></a><span data-ttu-id="80a0b-102">&lt;httpListener&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="80a0b-102">&lt;httpListener&gt; Element (Network Settings)</span></span>
<span data-ttu-id="80a0b-103">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="80a0b-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="80a0b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="80a0b-104">\<configuration></span></span>  
<span data-ttu-id="80a0b-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="80a0b-105">\<system.net></span></span>  
<span data-ttu-id="80a0b-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="80a0b-106">\<settings></span></span>  
<span data-ttu-id="80a0b-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="80a0b-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80a0b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80a0b-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="80a0b-109">Typ</span><span class="sxs-lookup"><span data-stu-id="80a0b-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80a0b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80a0b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="80a0b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80a0b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80a0b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="80a0b-112">Attributes</span></span>  
  
|<span data-ttu-id="80a0b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="80a0b-113">Attribute</span></span>|<span data-ttu-id="80a0b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="80a0b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80a0b-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="80a0b-115">unescapeRequestUrl</span></span>|<span data-ttu-id="80a0b-116">Logická hodnota, která označuje, pokud <xref:System.Net.HttpListener> instance používá nezpracovaná neuvozené URI místo převedený identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80a0b-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80a0b-117">Child Elements</span></span>  
 <span data-ttu-id="80a0b-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="80a0b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80a0b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80a0b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="80a0b-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="80a0b-120">**Element**</span></span>|<span data-ttu-id="80a0b-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="80a0b-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="80a0b-122">nastavení</span><span class="sxs-lookup"><span data-stu-id="80a0b-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="80a0b-123">Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="80a0b-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80a0b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80a0b-124">Remarks</span></span>  
 <span data-ttu-id="80a0b-125">**UnescapeRequestUrl** atribut uvádí, pokud <xref:System.Net.HttpListener> místo převedený identifikátor URI, kde se převedou všechny hodnoty kódováním procent a jsou přesměrováni další kroky normalizaci používá nezpracovaná neuvozené identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="80a0b-126">Když <xref:System.Net.HttpListener> instance obdrží žádost prostřednictvím `http.sys` služby, vytvoří instanci řetězce identifikátoru URI poskytuje `http.sys`a zpřístupní ho jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80a0b-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="80a0b-127">`http.sys` Service poskytuje dva řetězce identifikátoru URI žádosti:</span><span class="sxs-lookup"><span data-stu-id="80a0b-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="80a0b-128">Nezpracovaná URI</span><span class="sxs-lookup"><span data-stu-id="80a0b-128">Raw URI</span></span>  
  
-   <span data-ttu-id="80a0b-129">Převedený URI</span><span class="sxs-lookup"><span data-stu-id="80a0b-129">Converted URI</span></span>  
  
 <span data-ttu-id="80a0b-130">Je identifikátor URI, nezpracovaná <xref:System.Uri?displayProperty=nameWithType> uvedené v řádku žádosti požadavku HTTP:</span><span class="sxs-lookup"><span data-stu-id="80a0b-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="80a0b-131">Nezpracovaná URI poskytované `http.sys` pro požadavek uvedených výše, je "/ cesta /".</span><span class="sxs-lookup"><span data-stu-id="80a0b-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="80a0b-132">To představuje řetězec následující příkaz protokolu HTTP, protože byla odeslána po síti.</span><span class="sxs-lookup"><span data-stu-id="80a0b-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="80a0b-133">`http.sys` Service vytvoří převedený URI z informací uvedených v žádosti pomocí identifikátoru URI uvedené v řádku požadavku HTTP a předáte hlavičku hostitele k určení požadavku na zdrojový server.</span><span class="sxs-lookup"><span data-stu-id="80a0b-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="80a0b-134">Děje se tak, že porovnáte informace z požadavku sadu registrovaných předpony identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="80a0b-135">V dokumentaci sady SDK serveru HTTP označuje jako strukturu HTTP_COOKED_URL tento převedený identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="80a0b-136">Aby bylo možné k porovnání požadavek s registrované předpony identifikátoru URI, je třeba provést některé normalizaci na požadavek.</span><span class="sxs-lookup"><span data-stu-id="80a0b-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="80a0b-137">Pro ukázku výše převedený URI vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="80a0b-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="80a0b-138">`http.sys` Služby kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> hodnotu vlastnosti a řetězce v požadavku řádku k vytvoření převedený URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="80a0b-139">Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> třída také provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="80a0b-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="80a0b-140">Zrušení – řídicí sekvence kódovaného všechny procentuální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="80a0b-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="80a0b-141">Převede kódováním procent jiné znaky než ASCII do znázornění UTF-16 znaků.</span><span class="sxs-lookup"><span data-stu-id="80a0b-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="80a0b-142">Všimněte si, že znaky znakové sady UTF-8 a ANSI/DBCS se podporují i znaky znakové sady Unicode (kódování Unicode v formátu uXXXX %).</span><span class="sxs-lookup"><span data-stu-id="80a0b-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="80a0b-143">Spustí další kroky normalizaci, jako cesta komprese.</span><span class="sxs-lookup"><span data-stu-id="80a0b-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="80a0b-144">Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování použité pro kódování v procentech hodnoty, nemusí být možné určit správné kódování právě analýzou hodnoty kódováním procent.</span><span class="sxs-lookup"><span data-stu-id="80a0b-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="80a0b-145">Proto `http.sys` poskytuje dva klíče registru pro úpravy proces:</span><span class="sxs-lookup"><span data-stu-id="80a0b-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="80a0b-146">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="80a0b-146">Registry Key</span></span>|<span data-ttu-id="80a0b-147">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="80a0b-147">Default Value</span></span>|<span data-ttu-id="80a0b-148">Popis</span><span class="sxs-lookup"><span data-stu-id="80a0b-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="80a0b-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="80a0b-149">EnableNonUTF8</span></span>|<span data-ttu-id="80a0b-150">1</span><span class="sxs-lookup"><span data-stu-id="80a0b-150">1</span></span>|<span data-ttu-id="80a0b-151">Pokud nula, `http.sys` přijímá jenom kódování UTF-8 adresy URL.</span><span class="sxs-lookup"><span data-stu-id="80a0b-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="80a0b-152">Pokud nulová, `http.sys` také přijímá kódování ANSI nebo kódováním DBCS adresy URL v žádosti.</span><span class="sxs-lookup"><span data-stu-id="80a0b-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="80a0b-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="80a0b-153">FavorUTF8</span></span>|<span data-ttu-id="80a0b-154">1</span><span class="sxs-lookup"><span data-stu-id="80a0b-154">1</span></span>|<span data-ttu-id="80a0b-155">Pokud nulová, `http.sys` vždy pokusí dekódovat adresu URL jako UTF-8 nejprve; Pokud tento převod selže a EnableNonUTF8 je nulová, ovladač Http.sys potom pokusí dekódovat jako ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="80a0b-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="80a0b-156">Pokud nula (a EnableNonUTF8 je nulová), `http.sys` pokusí dekódovat jako ANSI nebo DBCS; Pokud tento není úspěšné, se pokusí o převodu znakové sady UTF-8.</span><span class="sxs-lookup"><span data-stu-id="80a0b-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="80a0b-157">Když <xref:System.Net.HttpListener> přijme požadavek, používá převedený URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80a0b-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="80a0b-158">Je třeba pro podporu znaky kromě znaky a čísla v identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="80a0b-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="80a0b-159">Následující identifikátor URI, který se používá k načtení informací o zákazníka pro zákazníka je například číslo "1/3812":</span><span class="sxs-lookup"><span data-stu-id="80a0b-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="80a0b-160">Poznámka: lomítko kódováním procent v identifikátoru Uri (% 2F).</span><span class="sxs-lookup"><span data-stu-id="80a0b-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="80a0b-161">To je nutné, protože v takovém případě lomítko představuje data a ne cesta oddělovač.</span><span class="sxs-lookup"><span data-stu-id="80a0b-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="80a0b-162">Předání řetězec Uri konstruktor povede k identifikátoru URI následující:</span><span class="sxs-lookup"><span data-stu-id="80a0b-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="80a0b-163">Rozdělení do jeho segmentů cesty by mělo za následek následující prvky:</span><span class="sxs-lookup"><span data-stu-id="80a0b-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="80a0b-164">Nejedná se o záměr odesílatel požadavku.</span><span class="sxs-lookup"><span data-stu-id="80a0b-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="80a0b-165">Pokud **unescapeRequestUrl** je atribut nastaven na **false**, pak když <xref:System.Net.HttpListener> přijme požadavek, používá nezpracovaná URI místo převedený URI z `http.sys` jako vstup <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80a0b-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="80a0b-166">Výchozí hodnota **unescapeRequestUrl** atribut je **true**.</span><span class="sxs-lookup"><span data-stu-id="80a0b-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="80a0b-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Vlastnost lze použít k získání aktuální hodnota **unescapeRequestUrl** atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="80a0b-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80a0b-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="80a0b-168">Example</span></span>  
 <span data-ttu-id="80a0b-169">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net.HttpListener> třídy, pokud obdrží požadavek na místo převedený URI z používat nezpracovaná URI `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="80a0b-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="80a0b-170">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="80a0b-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="80a0b-171">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="80a0b-171">Namespace</span></span>|<span data-ttu-id="80a0b-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="80a0b-172">System.Net</span></span>|  
|<span data-ttu-id="80a0b-173">Název schématu</span><span class="sxs-lookup"><span data-stu-id="80a0b-173">Schema Name</span></span>||  
|<span data-ttu-id="80a0b-174">Ověření souboru</span><span class="sxs-lookup"><span data-stu-id="80a0b-174">Validation File</span></span>||  
|<span data-ttu-id="80a0b-175">Může být prázdný</span><span class="sxs-lookup"><span data-stu-id="80a0b-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="80a0b-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="80a0b-176">See Also</span></span>  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [<span data-ttu-id="80a0b-177">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="80a0b-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
