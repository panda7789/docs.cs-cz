---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088378"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="b16b7-102">\<httpListener> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b16b7-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="b16b7-103">Přizpůsobuje parametry používané <xref:System.Net.HttpListener> třídou.</span><span class="sxs-lookup"><span data-stu-id="b16b7-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="b16b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b16b7-104">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="b16b7-105">Typ</span><span class="sxs-lookup"><span data-stu-id="b16b7-105">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b16b7-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b16b7-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b16b7-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b16b7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b16b7-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b16b7-108">Attributes</span></span>  
  
|<span data-ttu-id="b16b7-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="b16b7-109">Attribute</span></span>|<span data-ttu-id="b16b7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b16b7-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b16b7-111">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="b16b7-111">unescapeRequestUrl</span></span>|<span data-ttu-id="b16b7-112">Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b16b7-112">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b16b7-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b16b7-113">Child Elements</span></span>  
 <span data-ttu-id="b16b7-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="b16b7-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b16b7-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b16b7-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b16b7-116">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="b16b7-116">**Element**</span></span>|<span data-ttu-id="b16b7-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b16b7-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b16b7-118">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="b16b7-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b16b7-119">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b16b7-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b16b7-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b16b7-120">Remarks</span></span>  
 <span data-ttu-id="b16b7-121">Atribut **UnescapeRequestUrl** označuje, zda <xref:System.Net.HttpListener> Nástroj používá nezpracovaný identifikátor URI bez řídicího znaku namísto převedeného identifikátoru URI, ve kterém jsou převáděny všechny hodnoty zakódované v procentech a provedeny další kroky normalizace.</span><span class="sxs-lookup"><span data-stu-id="b16b7-121">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="b16b7-122">Když <xref:System.Net.HttpListener> instance obdrží požadavek přes `http.sys` službu, vytvoří instanci řetězce identifikátoru URI, kterou poskytuje `http.sys` , a zpřístupní ji jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b16b7-122">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="b16b7-123">`http.sys`Služba zpřístupňuje dva řetězce identifikátoru URI žádosti:</span><span class="sxs-lookup"><span data-stu-id="b16b7-123">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="b16b7-124">Nezpracovaný identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="b16b7-124">Raw URI</span></span>  
  
- <span data-ttu-id="b16b7-125">Převedený identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="b16b7-125">Converted URI</span></span>  
  
 <span data-ttu-id="b16b7-126">Nezpracovaný identifikátor URI je <xref:System.Uri?displayProperty=nameWithType> uvedený na řádku požadavku požadavku http:</span><span class="sxs-lookup"><span data-stu-id="b16b7-126">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="b16b7-127">Nezpracovaný identifikátor URI poskytnutý `http.sys` pro výše zmíněnou žádost je "/path/".</span><span class="sxs-lookup"><span data-stu-id="b16b7-127">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="b16b7-128">To představuje řetězec, který následuje za příkazem HTTP, jak byl odeslán přes síť.</span><span class="sxs-lookup"><span data-stu-id="b16b7-128">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="b16b7-129">`http.sys`Služba vytvoří převedený identifikátor URI z informací uvedených v žádosti pomocí identifikátoru URI, který je k dispozici na řádku požadavku HTTP a hlavičce hostitele k určení serveru původu, na který má být požadavek předán.</span><span class="sxs-lookup"><span data-stu-id="b16b7-129">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="b16b7-130">To se provádí porovnáním informací z požadavku se sadou registrovaných předpon identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="b16b7-130">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="b16b7-131">Dokumentace k sadě SDK serveru HTTP odkazuje na tento identifikátor URI, který je převedený jako struktura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="b16b7-131">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="b16b7-132">Aby bylo možné porovnat požadavek s registrovanými předponami identifikátoru URI, je nutné provést určitou normalizaci žádosti.</span><span class="sxs-lookup"><span data-stu-id="b16b7-132">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="b16b7-133">Pro ukázku nad převedený identifikátor URI by byl následující:</span><span class="sxs-lookup"><span data-stu-id="b16b7-133">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="b16b7-134">`http.sys`Služba kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> hodnotu vlastnosti a řetězec na řádku požadavku k vytvoření PŘEVEDENého identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b16b7-134">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="b16b7-135">Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> Třída provede také následující:</span><span class="sxs-lookup"><span data-stu-id="b16b7-135">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="b16b7-136">Zruší řídicí znaky všech hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="b16b7-136">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="b16b7-137">Převede znaky, které nejsou zakódované v procentech, do reprezentace znaků UTF-16.</span><span class="sxs-lookup"><span data-stu-id="b16b7-137">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="b16b7-138">Všimněte si, že se podporují znakové sady UTF-8 a ANSI/DBCS a také znaky Unicode (kódování Unicode pomocí formátu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="b16b7-138">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="b16b7-139">Provede další kroky normalizace, jako je komprese cesty.</span><span class="sxs-lookup"><span data-stu-id="b16b7-139">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="b16b7-140">Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování používaném v procentech zakódovaných hodnot, nemusí být možné určit správné kódování pouhým analýzou hodnot kódovaných v procentech.</span><span class="sxs-lookup"><span data-stu-id="b16b7-140">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="b16b7-141">Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:</span><span class="sxs-lookup"><span data-stu-id="b16b7-141">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="b16b7-142">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="b16b7-142">Registry Key</span></span>|<span data-ttu-id="b16b7-143">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="b16b7-143">Default Value</span></span>|<span data-ttu-id="b16b7-144">Description</span><span class="sxs-lookup"><span data-stu-id="b16b7-144">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="b16b7-145">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="b16b7-145">EnableNonUTF8</span></span>|<span data-ttu-id="b16b7-146">1</span><span class="sxs-lookup"><span data-stu-id="b16b7-146">1</span></span>|<span data-ttu-id="b16b7-147">Pokud je nula, `http.sys` akceptuje pouze adresy URL kódované v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b16b7-147">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="b16b7-148">Pokud je hodnota nenulová, `http.sys` v požadavcích také přijímá adresy URL kódované v kódování ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="b16b7-148">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="b16b7-149">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="b16b7-149">FavorUTF8</span></span>|<span data-ttu-id="b16b7-150">1</span><span class="sxs-lookup"><span data-stu-id="b16b7-150">1</span></span>|<span data-ttu-id="b16b7-151">Pokud je hodnota nenulová, `http.sys` vždy se pokusí dekódovat adresu URL jako znakovou sadu UTF-8. Pokud se převod nezdařil a EnableNonUTF8 je nenulový, http. sys, pokusí se ho dekódovat jako ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="b16b7-151">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="b16b7-152">Pokud je nula (a EnableNonUTF8 není nula), `http.sys` pokusí se dekódovat jako ANSI nebo DBCS; Pokud to není úspěšné, pokusí se převod znakové sady UTF-8.</span><span class="sxs-lookup"><span data-stu-id="b16b7-152">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="b16b7-153">Když aplikace <xref:System.Net.HttpListener> obdrží požadavek, použije převedený identifikátor URI z `http.sys` as Input na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b16b7-153">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="b16b7-154">V identifikátorech URI je potřeba podporovat znaky kromě znaků a číslic.</span><span class="sxs-lookup"><span data-stu-id="b16b7-154">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="b16b7-155">Příkladem je následující identifikátor URI, který se používá k načtení informací o zákaznících pro číslo zákazníka "1/3812":</span><span class="sxs-lookup"><span data-stu-id="b16b7-155">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="b16b7-156">Poznamenejte si procento lomítka v identifikátoru URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="b16b7-156">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="b16b7-157">To je nezbytné, protože v tomto případě znak lomítka představuje data a není oddělovačem cesty.</span><span class="sxs-lookup"><span data-stu-id="b16b7-157">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="b16b7-158">Předání řetězce do konstruktoru identifikátoru URI vede k následujícímu identifikátoru URI:</span><span class="sxs-lookup"><span data-stu-id="b16b7-158">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="b16b7-159">Rozdělení cesty k jeho segmentům by vedlo k následujícím prvkům:</span><span class="sxs-lookup"><span data-stu-id="b16b7-159">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="b16b7-160">Nejedná se o záměr odesilatele žádosti.</span><span class="sxs-lookup"><span data-stu-id="b16b7-160">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="b16b7-161">Pokud je atribut **UnescapeRequestUrl** nastaven na **hodnotu false**, pak při <xref:System.Net.HttpListener> přijetí žádosti použije nezpracovaný identifikátor URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b16b7-161">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="b16b7-162">Výchozí hodnota pro atribut **UnescapeRequestUrl** je **true**.</span><span class="sxs-lookup"><span data-stu-id="b16b7-162">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="b16b7-163"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Vlastnost lze použít k získání aktuální hodnoty atributu **UnescapeRequestUrl** z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="b16b7-163">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b16b7-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="b16b7-164">Example</span></span>  
 <span data-ttu-id="b16b7-165">Následující příklad ukazuje, jak nakonfigurovat třídu, <xref:System.Net.HttpListener> když obdrží požadavek na použití nezpracovaného identifikátoru URI namísto převedeného identifikátoru URI z `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b16b7-165">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="b16b7-166">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="b16b7-166">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="b16b7-167">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b16b7-167">Namespace</span></span>|<span data-ttu-id="b16b7-168">System.Net</span><span class="sxs-lookup"><span data-stu-id="b16b7-168">System.Net</span></span>|  
|<span data-ttu-id="b16b7-169">Název schématu</span><span class="sxs-lookup"><span data-stu-id="b16b7-169">Schema Name</span></span>||  
|<span data-ttu-id="b16b7-170">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="b16b7-170">Validation File</span></span>||  
|<span data-ttu-id="b16b7-171">Může být prázdné</span><span class="sxs-lookup"><span data-stu-id="b16b7-171">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="b16b7-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="b16b7-172">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="b16b7-173">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b16b7-173">Network Settings Schema</span></span>](index.md)
