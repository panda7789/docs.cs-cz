---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 5fe2eafee702be96bfdca80a06af4a040d9ef0f6
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664123"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="db880-102">\<Element > IDN (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="db880-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="db880-103">Určuje, jestli se má pro název domény použít analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="db880-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="db880-104">Hierarchie schématu</span><span class="sxs-lookup"><span data-stu-id="db880-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="db880-105">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="db880-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="db880-106">\<Identifikátor URI > – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="db880-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="db880-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="db880-107">\<idn></span></span>](idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="db880-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db880-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db880-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db880-109">Attributes and Elements</span></span>  
 <span data-ttu-id="db880-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db880-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db880-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="db880-111">Attributes</span></span>  
  
|<span data-ttu-id="db880-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="db880-112">**Element**</span></span>|<span data-ttu-id="db880-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="db880-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="db880-114">Určuje, jestli se pro název domény použije analýza v mezinárodní doméně (IDN). výchozí hodnota je None.</span><span class="sxs-lookup"><span data-stu-id="db880-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db880-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db880-115">Child Elements</span></span>  
 <span data-ttu-id="db880-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="db880-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db880-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db880-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db880-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="db880-118">**Element**</span></span>|<span data-ttu-id="db880-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="db880-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="db880-120">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="db880-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="db880-121">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="db880-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db880-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db880-122">Remarks</span></span>  
 <span data-ttu-id="db880-123">Existující <xref:System.Uri> třída se rozšířila v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="db880-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="db880-124">3,0 SP1 a 2,0 SP1 s podporou pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="db880-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="db880-125">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="db880-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="db880-126">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db880-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="db880-127">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="db880-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="db880-128">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="db880-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="db880-129">Určete, jestli se má pro název domény použít analýza v mezinárodní doméně (IDN) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="db880-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="db880-130">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="db880-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="db880-131">Existují tři možné hodnoty pro IDN v závislosti na používaných serverech DNS:</span><span class="sxs-lookup"><span data-stu-id="db880-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="db880-132">IDN povolené = vše</span><span class="sxs-lookup"><span data-stu-id="db880-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="db880-133">Tato hodnota převede všechny názvy domén Unicode na jejich ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="db880-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="db880-134">povolené IDN = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="db880-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="db880-135">Tato hodnota převede všechny názvy domén Unicode, které nejsou v místním intranetu, aby používaly ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="db880-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="db880-136">V tomto případě by se měly servery DNS, které se používají pro intranet, podporovat rozlišení názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="db880-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="db880-137">povoleno IDN = None</span><span class="sxs-lookup"><span data-stu-id="db880-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="db880-138">Tato hodnota nepřevede žádné názvy domén Unicode tak, aby používaly Punycode.</span><span class="sxs-lookup"><span data-stu-id="db880-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="db880-139">Jedná se o výchozí hodnotu, která je konzistentní s chováním .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="db880-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="db880-140">Povolením IDN převedete všechny jmenovky Unicode v názvu domény na jejich ekvivalenty Punycode.</span><span class="sxs-lookup"><span data-stu-id="db880-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="db880-141">Názvy Punycode obsahují pouze znaky ASCII a vždy začínají předponou Xn---prefix.</span><span class="sxs-lookup"><span data-stu-id="db880-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="db880-142">Důvodem je podpora stávajících serverů DNS na internetu, protože většina serverů DNS podporuje jenom znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="db880-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="db880-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="db880-143">Configuration Files</span></span>  
 <span data-ttu-id="db880-144">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="db880-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db880-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="db880-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="db880-146">Popis</span><span class="sxs-lookup"><span data-stu-id="db880-146">Description</span></span>  
 <span data-ttu-id="db880-147">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> třída používá pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="db880-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="db880-148">Kód</span><span class="sxs-lookup"><span data-stu-id="db880-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db880-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db880-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="db880-150">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="db880-150">Network Settings Schema</span></span>](index.md)
