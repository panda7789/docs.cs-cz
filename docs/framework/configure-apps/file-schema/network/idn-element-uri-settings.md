---
title: '&lt;IDN&gt; – Element (nastavení Uri)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 21950beeefb23e81066623534774148e1f5d92ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580733"
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="e38c3-102">&lt;IDN&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="e38c3-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="e38c3-103">Určuje, pokud analýza mezinárodních názvů domén (IDN) se použije na název domény.</span><span class="sxs-lookup"><span data-stu-id="e38c3-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="e38c3-104">Schema Hierarchy</span><span class="sxs-lookup"><span data-stu-id="e38c3-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="e38c3-105">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="e38c3-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="e38c3-106">\<Identifikátor URI > – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="e38c3-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="e38c3-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="e38c3-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="e38c3-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e38c3-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e38c3-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e38c3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e38c3-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e38c3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e38c3-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e38c3-111">Attributes</span></span>  
  
|<span data-ttu-id="e38c3-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="e38c3-112">**Element**</span></span>|<span data-ttu-id="e38c3-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e38c3-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="e38c3-114">Určuje, že jestli parsování mezinárodních názvů domén (IDN) se použije pro název domény výchozí hodnota je none.</span><span class="sxs-lookup"><span data-stu-id="e38c3-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e38c3-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e38c3-115">Child Elements</span></span>  
 <span data-ttu-id="e38c3-116">Žádná</span><span class="sxs-lookup"><span data-stu-id="e38c3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e38c3-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e38c3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e38c3-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e38c3-118">**Element**</span></span>|<span data-ttu-id="e38c3-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e38c3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e38c3-120">uri</span><span class="sxs-lookup"><span data-stu-id="e38c3-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="e38c3-121">Obsahuje nastavení, které určují způsob, jakým rozhraní .NET Framework zpracovává webové adresy vyjádřena pomocí uniform resource Identifier (identifikátory URI).</span><span class="sxs-lookup"><span data-stu-id="e38c3-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e38c3-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e38c3-122">Remarks</span></span>  
 <span data-ttu-id="e38c3-123">Existující <xref:System.Uri> bylo rozšířeno třídy v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="e38c3-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="e38c3-124">3.0 SP1 a 2.0 SP1 s podporou International Resource identifikátory (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="e38c3-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="e38c3-125">Aktuální uživatelé neuvidí žádné změny v chování rozhraní .NET Framework 2.0, pokud výslovně povolit IRI a IDN podporovat.</span><span class="sxs-lookup"><span data-stu-id="e38c3-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="e38c3-126">Tím se zajistí kompatibilitu aplikací se staršími verzemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e38c3-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="e38c3-127">Povolení podpory pro IRI, jsou požadovány následující dvě změny:</span><span class="sxs-lookup"><span data-stu-id="e38c3-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="e38c3-128">Přidejte následující řádek do souboru machine.config, v adresáři rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="e38c3-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="e38c3-129">Zadejte, jestli chcete parsování mezinárodních názvů domén (IDN) k názvu domény a určuje, zda by měl použít IRI pravidel pro analýzu.</span><span class="sxs-lookup"><span data-stu-id="e38c3-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="e38c3-130">To můžete udělat v souboru machine.config nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="e38c3-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="e38c3-131">Existují tři možné hodnoty pro IDN v závislosti na servery DNS, které se používají:</span><span class="sxs-lookup"><span data-stu-id="e38c3-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="e38c3-132">IDN, povoleno = All</span><span class="sxs-lookup"><span data-stu-id="e38c3-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="e38c3-133">Tato hodnota se převede názvy domén, Unicode na jejich ekvivalenty kódování Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="e38c3-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="e38c3-134">IDN, povoleno = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="e38c3-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="e38c3-135">Tato hodnota se převede všechny názvy domén Unicode nejsou v místním intranetu používat kódování Punycode ekvivalenty (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="e38c3-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="e38c3-136">V tomto případě zpracování mezinárodních názvů na místní Intranet, které se používají pro intranetové servery DNS by měly podporovat překlad kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="e38c3-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="e38c3-137">IDN, povoleno = None</span><span class="sxs-lookup"><span data-stu-id="e38c3-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="e38c3-138">Tato hodnota neprovede konverzi názvy domén, Unicode používat kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="e38c3-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="e38c3-139">Toto je výchozí hodnota je shodný se chování rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="e38c3-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="e38c3-140">Povolení IDN převede všechny popisky kódování Unicode v názvu domény na jejich ekvivalenty kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="e38c3-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="e38c3-141">Kódování Punycode názvy obsahovat pouze znaky ASCII a vždy začínají předponou xn –.</span><span class="sxs-lookup"><span data-stu-id="e38c3-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="e38c3-142">Důvodem je k podpoře existujících serverů DNS na Internetu, protože většina servery DNS podporují jenom znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="e38c3-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="e38c3-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e38c3-143">Configuration Files</span></span>  
 <span data-ttu-id="e38c3-144">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e38c3-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e38c3-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="e38c3-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e38c3-146">Popis</span><span class="sxs-lookup"><span data-stu-id="e38c3-146">Description</span></span>  
 <span data-ttu-id="e38c3-147">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýza IRI a názvy IDN.</span><span class="sxs-lookup"><span data-stu-id="e38c3-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e38c3-148">Kód</span><span class="sxs-lookup"><span data-stu-id="e38c3-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e38c3-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e38c3-149">See also</span></span>
- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="e38c3-150">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e38c3-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
