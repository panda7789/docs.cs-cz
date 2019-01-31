---
title: <httpListener> – element (nastavení sítě)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: ff5e4ad2788ab3df621beb52b1703647df068a7f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257990"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="dfc84-102">\<httpListener > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="dfc84-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="dfc84-103">Přizpůsobí parametrů používaných <xref:System.Net.HttpListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfc84-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="dfc84-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="dfc84-104">\<configuration></span></span>  
<span data-ttu-id="dfc84-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="dfc84-105">\<system.net></span></span>  
<span data-ttu-id="dfc84-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="dfc84-106">\<settings></span></span>  
<span data-ttu-id="dfc84-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="dfc84-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc84-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfc84-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="dfc84-109">Typ</span><span class="sxs-lookup"><span data-stu-id="dfc84-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfc84-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dfc84-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dfc84-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dfc84-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfc84-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="dfc84-112">Attributes</span></span>  
  
|<span data-ttu-id="dfc84-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="dfc84-113">Attribute</span></span>|<span data-ttu-id="dfc84-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dfc84-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfc84-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="dfc84-115">unescapeRequestUrl</span></span>|<span data-ttu-id="dfc84-116">Logická hodnota, která označuje, zda <xref:System.Net.HttpListener> instance používá nezpracovaná neuvozené identifikátor URI namísto převedený identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="dfc84-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfc84-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dfc84-117">Child Elements</span></span>  
 <span data-ttu-id="dfc84-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="dfc84-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfc84-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dfc84-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dfc84-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="dfc84-120">**Element**</span></span>|<span data-ttu-id="dfc84-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="dfc84-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="dfc84-122">settings</span><span class="sxs-lookup"><span data-stu-id="dfc84-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="dfc84-123">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dfc84-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfc84-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfc84-124">Remarks</span></span>  
 <span data-ttu-id="dfc84-125">**UnescapeRequestUrl** atribut označuje, zda <xref:System.Net.HttpListener> používá nezpracovaná neuvozené identifikátor URI namísto převedený identifikátor URI, kde všechny procentuálně zakódovaný hodnoty se převedou a ostatní kroky normalizace pocházejí.</span><span class="sxs-lookup"><span data-stu-id="dfc84-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="dfc84-126">Když <xref:System.Net.HttpListener> instance obdrží žádost prostřednictvím `http.sys` služby, vytvoří instanci řetězec identifikátoru URI poskytuje `http.sys`a zpřístupní ho jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dfc84-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="dfc84-127">`http.sys` Služba poskytuje dva řetězce identifikátoru URI požadavku:</span><span class="sxs-lookup"><span data-stu-id="dfc84-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="dfc84-128">Identifikátor URI nezpracované</span><span class="sxs-lookup"><span data-stu-id="dfc84-128">Raw URI</span></span>  
  
-   <span data-ttu-id="dfc84-129">Převedený identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="dfc84-129">Converted URI</span></span>  
  
 <span data-ttu-id="dfc84-130">Identifikátor URI nezpracované <xref:System.Uri?displayProperty=nameWithType> v řádku žádosti požadavku HTTP:</span><span class="sxs-lookup"><span data-stu-id="dfc84-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="dfc84-131">Nezpracovaná URI poskytuje `http.sys` pro požadavek uvedených výše, je "/ cesta /".</span><span class="sxs-lookup"><span data-stu-id="dfc84-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="dfc84-132">To představuje řetězec po příkaz HTTP byl odeslán přes síť.</span><span class="sxs-lookup"><span data-stu-id="dfc84-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="dfc84-133">`http.sys` Služby vytvoří převedený identifikátor URI z informací uvedených v požadavku pomocí identifikátoru URI k dispozici v řádku požadavku HTTP a mají předávat hlavičku hostitele k určení požadavku na zdrojový server.</span><span class="sxs-lookup"><span data-stu-id="dfc84-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="dfc84-134">To se provádí porovnáváním informací z požadavku sadu registrovaných předpony identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="dfc84-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="dfc84-135">Dokumentace ke službě SDK serveru HTTP odkazuje na tento identifikátor URI převedený jako HTTP_COOKED_URL struktury.</span><span class="sxs-lookup"><span data-stu-id="dfc84-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="dfc84-136">Aby bylo možné porovnat požadavek s registrované předpony identifikátoru URI, je potřeba udělat nějaké normalizace na požadavek.</span><span class="sxs-lookup"><span data-stu-id="dfc84-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="dfc84-137">Pro ukázku nad převedený identifikátoru URI by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dfc84-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="dfc84-138">`http.sys` Služby kombinuje <xref:System.Uri.Host%2A?displayProperty=nameWithType> řetězec v řádku žádost o vytvoření převedený identifikátor URI a hodnota vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dfc84-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="dfc84-139">Kromě toho `http.sys` a <xref:System.Uri?displayProperty=nameWithType> třída rovněž provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="dfc84-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="dfc84-140">Zrušit – řídicí sekvence kódovaného všechny procentuální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dfc84-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="dfc84-141">Převede procentuálně zakódovaný jiné znaky než ASCII na reprezentaci znaků UTF-16.</span><span class="sxs-lookup"><span data-stu-id="dfc84-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="dfc84-142">Všimněte si, že jsou podporovány UTF-8 a ANSI/DBCS znaky a znaky kódování Unicode (kódování Unicode ve formátu uXXXX %).</span><span class="sxs-lookup"><span data-stu-id="dfc84-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="dfc84-143">Spustí další kroky normalizace, jako je komprese cestu.</span><span class="sxs-lookup"><span data-stu-id="dfc84-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="dfc84-144">Vzhledem k tomu, že žádost neobsahuje žádné informace o kódování použité pro procentuálně zakódovaný hodnoty, nemusí být možné určit správné kódování pouhým Analýza hodnot procentuálně zakódovaný.</span><span class="sxs-lookup"><span data-stu-id="dfc84-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="dfc84-145">Proto `http.sys` poskytuje dva klíče registru pro úpravu procesu:</span><span class="sxs-lookup"><span data-stu-id="dfc84-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="dfc84-146">Klíč registru</span><span class="sxs-lookup"><span data-stu-id="dfc84-146">Registry Key</span></span>|<span data-ttu-id="dfc84-147">Výchozí hodnota</span><span class="sxs-lookup"><span data-stu-id="dfc84-147">Default Value</span></span>|<span data-ttu-id="dfc84-148">Popis</span><span class="sxs-lookup"><span data-stu-id="dfc84-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="dfc84-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="dfc84-149">EnableNonUTF8</span></span>|<span data-ttu-id="dfc84-150">1</span><span class="sxs-lookup"><span data-stu-id="dfc84-150">1</span></span>|<span data-ttu-id="dfc84-151">Pokud je nula, `http.sys` přijímá pouze adresy kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="dfc84-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="dfc84-152">Nenulová, pokud `http.sys` přijímá také kódovaný v ANSI nebo DBCS kódování adresy URL v požadavcích.</span><span class="sxs-lookup"><span data-stu-id="dfc84-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="dfc84-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="dfc84-153">FavorUTF8</span></span>|<span data-ttu-id="dfc84-154">1</span><span class="sxs-lookup"><span data-stu-id="dfc84-154">1</span></span>|<span data-ttu-id="dfc84-155">Nenulová, pokud `http.sys` vždy pokusí dekódování adresu URL jako UTF-8. Pokud se nepovede převodu a EnableNonUTF8 nenulové, ovladač Http.sys potom pokusí dekódovat jako ANSI nebo DBCS.</span><span class="sxs-lookup"><span data-stu-id="dfc84-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="dfc84-156">Pokud je nula (a EnableNonUTF8 zbývá nenulový), `http.sys` pokusí dekódovat jako ANSI nebo DBCS; Pokud to není úspěšné, pokusí převod kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="dfc84-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="dfc84-157">Když <xref:System.Net.HttpListener> obdrží žádost, používá převedený identifikátor URI ze `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dfc84-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="dfc84-158">Je potřeba pro podporu znaky kromě znaky a čísla v identifikátorech URI.</span><span class="sxs-lookup"><span data-stu-id="dfc84-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="dfc84-159">Příkladem je následující identifikátor URI, který slouží k načtení informací zákazníků pro zákazníka číslo "1/3812":</span><span class="sxs-lookup"><span data-stu-id="dfc84-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="dfc84-160">Všimněte si lomítko procentuálně zakódovaný v identifikátoru Uri (% 2F).</span><span class="sxs-lookup"><span data-stu-id="dfc84-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="dfc84-161">To je nezbytné, protože v tomto případě představuje znak lomítka dat a oddělovač cesty.</span><span class="sxs-lookup"><span data-stu-id="dfc84-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="dfc84-162">Předání řetězce identifikátoru Uri konstruktoru povede k následující identifikátor URI:</span><span class="sxs-lookup"><span data-stu-id="dfc84-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="dfc84-163">Rozdělení do jeho segmentů cesty by mít za následek následující prvky:</span><span class="sxs-lookup"><span data-stu-id="dfc84-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="dfc84-164">Toto není cílem odesílatel požadavku.</span><span class="sxs-lookup"><span data-stu-id="dfc84-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="dfc84-165">Pokud **unescapeRequestUrl** atribut je nastaven na **false**, pak když <xref:System.Net.HttpListener> obdrží žádost, používá nezpracovaná identifikátor URI namísto převedený identifikátor URI ze `http.sys` jako vstup <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dfc84-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="dfc84-166">Výchozí hodnota **unescapeRequestUrl** atribut je **true**.</span><span class="sxs-lookup"><span data-stu-id="dfc84-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="dfc84-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Vlastnost lze použít k získání aktuální hodnoty **unescapeRequestUrl** atribut z příslušných konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="dfc84-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfc84-168">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfc84-168">Example</span></span>  
 <span data-ttu-id="dfc84-169">Následující příklad ukazuje, jak nakonfigurovat <xref:System.Net.HttpListener> třídy, když přijme požadavek na identifikátor URI nezpracované nahrazujícím převedený identifikátor URI ze `http.sys` jako vstup na <xref:System.Net.HttpListenerRequest.Url%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dfc84-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="dfc84-170">Informace o elementu</span><span class="sxs-lookup"><span data-stu-id="dfc84-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="dfc84-171">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="dfc84-171">Namespace</span></span>|<span data-ttu-id="dfc84-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="dfc84-172">System.Net</span></span>|  
|<span data-ttu-id="dfc84-173">Název schématu</span><span class="sxs-lookup"><span data-stu-id="dfc84-173">Schema Name</span></span>||  
|<span data-ttu-id="dfc84-174">Soubor ověření</span><span class="sxs-lookup"><span data-stu-id="dfc84-174">Validation File</span></span>||  
|<span data-ttu-id="dfc84-175">Může být prázdné.</span><span class="sxs-lookup"><span data-stu-id="dfc84-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="dfc84-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfc84-176">See also</span></span>
- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="dfc84-177">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="dfc84-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
