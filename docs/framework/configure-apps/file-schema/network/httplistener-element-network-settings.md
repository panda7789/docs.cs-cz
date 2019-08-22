---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: cb24dc7296e2f2f6ea292566330d3d6ae4f25f85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664143"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="90736-102">\<httpListener – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="90736-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="90736-103">Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.</span><span class="sxs-lookup"><span data-stu-id="90736-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="90736-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="90736-104">\<configuration></span></span>  
<span data-ttu-id="90736-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="90736-105">\<system.net></span></span>  
<span data-ttu-id="90736-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="90736-106">\<settings></span></span>  
<span data-ttu-id="90736-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="90736-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90736-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90736-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="90736-109">type</span><span class="sxs-lookup"><span data-stu-id="90736-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90736-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90736-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90736-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="90736-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90736-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="90736-112">Attributes</span></span>  
  
|<span data-ttu-id="90736-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="90736-113">Attribute</span></span>|<span data-ttu-id="90736-114">Popis</span><span class="sxs-lookup"><span data-stu-id="90736-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90736-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="90736-115">unescapeRequestUrl</span></span>|<span data-ttu-id="90736-116">Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="90736-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90736-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90736-117">Child Elements</span></span>  
 <span data-ttu-id="90736-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="90736-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90736-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90736-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90736-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="90736-120">**Element**</span></span>|<span data-ttu-id="90736-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="90736-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="90736-122">možnost</span><span class="sxs-lookup"><span data-stu-id="90736-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="90736-123">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="90736-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90736-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90736-124">Remarks</span></span>  
 <span data-ttu-id="90736-125">Atribut **UnescapeRequestUrl** označuje, zda <xref:System.Net.HttpListener> nástroj používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI, ve kterém jsou převáděny všechny hodnoty zakódované v procentech a provedeny další kroky normalizace.</span><span class="sxs-lookup"><span data-stu-id="90736-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="90736-126">Když instance obdrží požadavek `http.sys` přes službu, vytvoří instanci řetězce identifikátoru URI, kterou `http.sys`poskytuje, a zpřístupní ji jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost. <xref:System.Net.HttpListener></span><span class="sxs-lookup"><span data-stu-id="90736-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="90736-127">`http.sys` Služba zpřístupňuje dva řetězce identifikátoru URI žádosti:</span><span class="sxs-lookup"><span data-stu-id="90736-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="90736-128">Nezpracovaný identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="90736-128">Raw URI</span></span>  
  
- <span data-ttu-id="90736-129">Převedený identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="90736-129">Converted URI</span></span>  
  
 <span data-ttu-id="90736-130">Nezpracovaný identifikátor URI je <xref:System.Uri?displayProperty=nameWithType> uvedený na řádku požadavku požadavku http:</span><span class="sxs-lookup"><span data-stu-id="90736-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="90736-131">Nezpracovaný identifikátor URI poskytnutý `http.sys` pro výše zmíněnou žádost je "/path/".</span><span class="sxs-lookup"><span data-stu-id="90736-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="90736-132">To představuje řetězec, který následuje za příkazem HTTP, jak byl odeslán přes síť.</span><span class="sxs-lookup"><span data-stu-id="90736-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="90736-133">`http.sys` Služba vytvoří převedený identifikátor URI z informací uvedených v žádosti pomocí identifikátoru URI, který je k dispozici na řádku požadavku HTTP a hlavičce hostitele k určení serveru původu, na který má být požadavek předán.</span><span class="sxs-lookup"><span data-stu-id="90736-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="90736-134">To se provádí porovnáním informací z požadavku se sadou registrovaných předpon identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="90736-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="90736-135">Dokumentace k sadě SDK serveru HTTP odkazuje na tento převedený identifikátor URI jako na strukturu HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="90736-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="90736-136">Aby bylo možné porovnat požadavek s registrovanými předponami identifikátoru URI, je nutné provést určitou normalizaci žádosti.</span><span class="sxs-lookup"><span data-stu-id="90736-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="90736-137">Pro ukázku nad převedený identifikátor URI by byl následující:</span><span class="sxs-lookup"><span data-stu-id="90736-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="90736-138">`http.sys` Služba kombinujehodnotuvlastnostiařetězecnařádkupožadavkukvytvořenípřevedeného<xref:System.Uri.Host%2A?displayProperty=nameWithType> identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="90736-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="90736-139">Kromě toho `http.sys` <xref:System.Uri?displayProperty=nameWithType> a Třída provede také následující:</span><span class="sxs-lookup"><span data-stu-id="90736-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="90736-140">Zruší řídicí znaky všech hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="90736-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="90736-141">Převede znaky, které nejsou zakódované v procentech, do reprezentace znaků UTF-16.</span><span class="sxs-lookup"><span data-stu-id="90736-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="90736-142">Všimněte si, že se podporují znakové sady UTF-8 a ANSI/DBCS a také znaky Unicode (kódování Unicode pomocí formátu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="90736-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="90736-143">Provede další kroky normalizace, jako je komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="90736-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="90736-144">Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování používaném v procentech zakódovaných hodnot, nemusí být možné určit správné kódování pouhým analýzou hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="90736-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="90736-145">Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:</span><span class="sxs-lookup"><span data-stu-id="90736-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="90736-146">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="90736-146">Registry Key</span></span>|<span data-ttu-id="90736-147">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="90736-147">Default Value</span></span>|<span data-ttu-id="90736-148">Popis</span><span class="sxs-lookup"><span data-stu-id="90736-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="90736-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="90736-149">EnableNonUTF8</span></span>|<span data-ttu-id="90736-150">1</span><span class="sxs-lookup"><span data-stu-id="90736-150">1</span></span>|<span data-ttu-id="90736-151">Pokud je nula `http.sys` , akceptuje pouze adresy URL kódované v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="90736-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="90736-152">Pokud je hodnota nenulová `http.sys` , v požadavcích také přijímá adresy URL kódované v kódování ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="90736-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="90736-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="90736-153">FavorUTF8</span></span>|<span data-ttu-id="90736-154">1</span><span class="sxs-lookup"><span data-stu-id="90736-154">1</span></span>|<span data-ttu-id="90736-155">Pokud je hodnota nenulová `http.sys` , vždy se pokusí dekódovat adresu URL jako znakovou sadu UTF-8. Pokud se převod nezdařil a EnableNonUTF8 je nenulový, http. sys, pokusí se ho dekódovat jako ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="90736-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="90736-156">Pokud je nula (a EnableNonUTF8 není nula), `http.sys` pokusí se dekódovat jako ANSI nebo DBCS; Pokud to není úspěšné, pokusí se převod znakové sady UTF-8.</span><span class="sxs-lookup"><span data-stu-id="90736-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="90736-157">Když <xref:System.Net.HttpListener> aplikace obdrží požadavek, použije převedený identifikátor URI `http.sys` z as Input na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90736-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="90736-158">V identifikátorech URI je potřeba podporovat znaky kromě znaků a číslic.</span><span class="sxs-lookup"><span data-stu-id="90736-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="90736-159">Příkladem je následující identifikátor URI, který se používá k načtení informací o zákaznících pro číslo zákazníka "1/3812":</span><span class="sxs-lookup"><span data-stu-id="90736-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="90736-160">Poznamenejte si procento lomítka v identifikátoru URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="90736-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="90736-161">To je nezbytné, protože v tomto případě znak lomítka představuje data a není oddělovačem cesty.</span><span class="sxs-lookup"><span data-stu-id="90736-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="90736-162">Předání řetězce do konstruktoru identifikátoru URI vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="90736-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="90736-163">Rozdělení cesty k jeho segmentům by vedlo k následujícím prvkům:</span><span class="sxs-lookup"><span data-stu-id="90736-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="90736-164">Nejedná se o záměr odesilatele žádosti.</span><span class="sxs-lookup"><span data-stu-id="90736-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="90736-165">Pokud je atribut **UnescapeRequestUrl** nastaven na **hodnotu false**, <xref:System.Net.HttpListener> pak při přijetí žádosti použije nezpracovaný identifikátor URI namísto převedeného <xref:System.Net.HttpListenerRequest.Url%2A> identifikátoru URI z `http.sys` jako vstup na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90736-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="90736-166">Výchozí hodnota pro atribut **UnescapeRequestUrl** je **true**.</span><span class="sxs-lookup"><span data-stu-id="90736-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="90736-167">Vlastnost lze použít k získání aktuální hodnoty atributu UnescapeRequestUrl z příslušných konfiguračních souborů. <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A></span><span class="sxs-lookup"><span data-stu-id="90736-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90736-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="90736-168">Example</span></span>  
 <span data-ttu-id="90736-169">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net.HttpListener> třídu, když obdrží požadavek na použití nezpracovaného identifikátoru URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="90736-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="90736-170">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="90736-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="90736-171">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="90736-171">Namespace</span></span>|<span data-ttu-id="90736-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="90736-172">System.Net</span></span>|  
|<span data-ttu-id="90736-173">Název schématu</span><span class="sxs-lookup"><span data-stu-id="90736-173">Schema Name</span></span>||  
|<span data-ttu-id="90736-174">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="90736-174">Validation File</span></span>||  
|<span data-ttu-id="90736-175">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="90736-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="90736-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90736-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="90736-177">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="90736-177">Network Settings Schema</span></span>](index.md)
