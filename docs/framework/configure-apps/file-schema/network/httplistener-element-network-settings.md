---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088378"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="e8da8-102">\<element > httpListener (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e8da8-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="e8da8-103">Přizpůsobuje parametry používané třídou <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

<span data-ttu-id="e8da8-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e8da8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e8da8-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8da8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="e8da8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nastavení >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="e8da8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="e8da8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpListener >**</span><span class="sxs-lookup"><span data-stu-id="e8da8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e8da8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8da8-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="e8da8-109">Typ</span><span class="sxs-lookup"><span data-stu-id="e8da8-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8da8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e8da8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e8da8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e8da8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8da8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e8da8-112">Attributes</span></span>  
  
|<span data-ttu-id="e8da8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e8da8-113">Attribute</span></span>|<span data-ttu-id="e8da8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e8da8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8da8-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="e8da8-115">unescapeRequestUrl</span></span>|<span data-ttu-id="e8da8-116">Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="e8da8-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8da8-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e8da8-117">Child Elements</span></span>  
 <span data-ttu-id="e8da8-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="e8da8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8da8-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e8da8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e8da8-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="e8da8-120">**Element**</span></span>|<span data-ttu-id="e8da8-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e8da8-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e8da8-122">možnost</span><span class="sxs-lookup"><span data-stu-id="e8da8-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="e8da8-123">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8da8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8da8-124">Remarks</span></span>  
 <span data-ttu-id="e8da8-125">Atribut **UnescapeRequestUrl** označuje, zda <xref:System.Net.HttpListener> používá nezpracovaný identifikátor URI bez řídicího znaku namísto PŘEVEDENého identifikátoru URI, kde jsou převáděny všechny hodnoty zakódované v procentech a jsou provedeny další kroky normalizace.</span><span class="sxs-lookup"><span data-stu-id="e8da8-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="e8da8-126">Když instance <xref:System.Net.HttpListener> obdrží požadavek prostřednictvím služby `http.sys`, vytvoří instanci řetězce identifikátoru URI, kterou poskytuje `http.sys`, a zpřístupní ji jako vlastnost <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="e8da8-127">Služba `http.sys` zpřístupňuje dva řetězce identifikátoru URI žádosti:</span><span class="sxs-lookup"><span data-stu-id="e8da8-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="e8da8-128">Nezpracovaný identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="e8da8-128">Raw URI</span></span>  
  
- <span data-ttu-id="e8da8-129">Převedený identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="e8da8-129">Converted URI</span></span>  
  
 <span data-ttu-id="e8da8-130">Nezpracovaný identifikátor URI je <xref:System.Uri?displayProperty=nameWithType>, který je k dispozici na řádku požadavku požadavku HTTP:</span><span class="sxs-lookup"><span data-stu-id="e8da8-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="e8da8-131">Nezpracovaný identifikátor URI poskytnutý `http.sys` pro výše uvedenou žádost je "/path/".</span><span class="sxs-lookup"><span data-stu-id="e8da8-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="e8da8-132">To představuje řetězec, který následuje za příkazem HTTP, jak byl odeslán přes síť.</span><span class="sxs-lookup"><span data-stu-id="e8da8-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="e8da8-133">Služba `http.sys` vytvoří převedený identifikátor URI z informací uvedených v žádosti pomocí identifikátoru URI, který je k dispozici na řádku požadavku HTTP a v hlavičce hostitele k určení serveru původu, na který má být požadavek předán.</span><span class="sxs-lookup"><span data-stu-id="e8da8-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="e8da8-134">To se provádí porovnáním informací z požadavku se sadou registrovaných předpon identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="e8da8-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="e8da8-135">Dokumentace k sadě SDK serveru HTTP odkazuje na tento identifikátor URI, který je převedený jako struktura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="e8da8-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="e8da8-136">Aby bylo možné porovnat požadavek s registrovanými předponami identifikátoru URI, je nutné provést určitou normalizaci žádosti.</span><span class="sxs-lookup"><span data-stu-id="e8da8-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="e8da8-137">Pro ukázku nad převedený identifikátor URI by byl následující:</span><span class="sxs-lookup"><span data-stu-id="e8da8-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="e8da8-138">Služba `http.sys` kombinuje hodnotu vlastnosti <xref:System.Uri.Host%2A?displayProperty=nameWithType> a řetězec na řádku požadavku k vytvoření převedeného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="e8da8-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="e8da8-139">Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> Třída provede také následující:</span><span class="sxs-lookup"><span data-stu-id="e8da8-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="e8da8-140">Zruší řídicí znaky všech hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="e8da8-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="e8da8-141">Převede znaky, které nejsou zakódované v procentech, do reprezentace znaků UTF-16.</span><span class="sxs-lookup"><span data-stu-id="e8da8-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="e8da8-142">Všimněte si, že se podporují znakové sady UTF-8 a ANSI/DBCS a také znaky Unicode (kódování Unicode pomocí formátu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="e8da8-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="e8da8-143">Provede další kroky normalizace, jako je komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="e8da8-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="e8da8-144">Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování používaném v procentech zakódovaných hodnot, nemusí být možné určit správné kódování pouhým analýzou hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="e8da8-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="e8da8-145">Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:</span><span class="sxs-lookup"><span data-stu-id="e8da8-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="e8da8-146">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="e8da8-146">Registry Key</span></span>|<span data-ttu-id="e8da8-147">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="e8da8-147">Default Value</span></span>|<span data-ttu-id="e8da8-148">Popis</span><span class="sxs-lookup"><span data-stu-id="e8da8-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="e8da8-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="e8da8-149">EnableNonUTF8</span></span>|<span data-ttu-id="e8da8-150">první</span><span class="sxs-lookup"><span data-stu-id="e8da8-150">1</span></span>|<span data-ttu-id="e8da8-151">Pokud je nula, `http.sys` přijímá pouze adresy URL kódované v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e8da8-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="e8da8-152">Pokud je hodnota nenulová, `http.sys` také v žádostech přijímat adresy URL kódované v kódování ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="e8da8-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="e8da8-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="e8da8-153">FavorUTF8</span></span>|<span data-ttu-id="e8da8-154">první</span><span class="sxs-lookup"><span data-stu-id="e8da8-154">1</span></span>|<span data-ttu-id="e8da8-155">Pokud není nula, `http.sys` se vždy pokusí dekódovat adresu URL jako UTF-8 First; Pokud se převod nezdařil a EnableNonUTF8 je nenulová, http. sys se pak pokusí dekódovat jako ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="e8da8-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="e8da8-156">Pokud je nula (a EnableNonUTF8 není nula), `http.sys` se pokusí dekódovat jako ANSI nebo DBCS; Pokud se to nepodaří, pokusí se převod UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e8da8-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="e8da8-157">Když <xref:System.Net.HttpListener> obdrží požadavek, použije převedený identifikátor URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="e8da8-158">V identifikátorech URI je potřeba podporovat znaky kromě znaků a číslic.</span><span class="sxs-lookup"><span data-stu-id="e8da8-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="e8da8-159">Příkladem je následující identifikátor URI, který se používá k načtení informací o zákaznících pro číslo zákazníka "1/3812":</span><span class="sxs-lookup"><span data-stu-id="e8da8-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="e8da8-160">Poznamenejte si procento lomítka v identifikátoru URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="e8da8-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="e8da8-161">To je nezbytné, protože v tomto případě znak lomítka představuje data a není oddělovačem cesty.</span><span class="sxs-lookup"><span data-stu-id="e8da8-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="e8da8-162">Předání řetězce do konstruktoru identifikátoru URI vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="e8da8-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="e8da8-163">Rozdělení cesty k jeho segmentům by vedlo k následujícím prvkům:</span><span class="sxs-lookup"><span data-stu-id="e8da8-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="e8da8-164">Nejedná se o záměr odesilatele žádosti.</span><span class="sxs-lookup"><span data-stu-id="e8da8-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="e8da8-165">Pokud je atribut **UnescapeRequestUrl** nastaven na **hodnotu false**, pak když <xref:System.Net.HttpListener> obdrží požadavek, použije nezpracovaný identifikátor URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="e8da8-166">Výchozí hodnota pro atribut **UnescapeRequestUrl** je **true**.</span><span class="sxs-lookup"><span data-stu-id="e8da8-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="e8da8-167">Vlastnost <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> lze použít k získání aktuální hodnoty atributu **UnescapeRequestUrl** z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="e8da8-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8da8-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8da8-168">Example</span></span>  
 <span data-ttu-id="e8da8-169">Následující příklad ukazuje, jak nakonfigurovat třídu <xref:System.Net.HttpListener>, když obdrží požadavek na použití nezpracovaného IDENTIFIKÁTORu URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na vlastnost <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="e8da8-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="e8da8-170">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="e8da8-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="e8da8-171">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e8da8-171">Namespace</span></span>|<span data-ttu-id="e8da8-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="e8da8-172">System.Net</span></span>|  
|<span data-ttu-id="e8da8-173">Název schématu</span><span class="sxs-lookup"><span data-stu-id="e8da8-173">Schema Name</span></span>||  
|<span data-ttu-id="e8da8-174">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="e8da8-174">Validation File</span></span>||  
|<span data-ttu-id="e8da8-175">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="e8da8-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e8da8-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8da8-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="e8da8-177">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e8da8-177">Network Settings Schema</span></span>](index.md)
