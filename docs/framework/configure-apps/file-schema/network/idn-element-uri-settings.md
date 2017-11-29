---
title: "&lt;IDN&gt; – Element (nastavení Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1f631f41c256e74e9b7bf7dc2d771ee156538820
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="72091-102">&lt;IDN&gt; – Element (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="72091-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="72091-103">Určuje, zda analýza mezinárodní název domény (IDN) je použita na název domény.</span><span class="sxs-lookup"><span data-stu-id="72091-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="72091-104">Schéma hierarchie</span><span class="sxs-lookup"><span data-stu-id="72091-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="72091-105">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="72091-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="72091-106">\<Identifikátor URI > elementu (nastavení Uri)</span><span class="sxs-lookup"><span data-stu-id="72091-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="72091-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="72091-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="72091-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72091-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72091-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72091-109">Attributes and Elements</span></span>  
 <span data-ttu-id="72091-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72091-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72091-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="72091-111">Attributes</span></span>  
  
|<span data-ttu-id="72091-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="72091-112">**Element**</span></span>|<span data-ttu-id="72091-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="72091-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="72091-114">Určuje, že pokud analýza mezinárodní název domény (IDN) se použije pro název domény výchozí hodnota je none.</span><span class="sxs-lookup"><span data-stu-id="72091-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72091-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72091-115">Child Elements</span></span>  
 <span data-ttu-id="72091-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="72091-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72091-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72091-117">Parent Elements</span></span>  
  
|<span data-ttu-id="72091-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="72091-118">**Element**</span></span>|<span data-ttu-id="72091-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="72091-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="72091-120">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="72091-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="72091-121">Obsahuje nastavení, které určují, jak rozhraní .NET Framework zpracovává webové adresy vyjádřit pomocí identifikátorů URI (URI).</span><span class="sxs-lookup"><span data-stu-id="72091-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72091-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72091-122">Remarks</span></span>  
 <span data-ttu-id="72091-123">Existující <xref:System.Uri> třída rozšířilo v rozhraní .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="72091-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="72091-124">3.0 SP1 a s podporou pro mezinárodní prostředků identifikátory (IRI) a mezinárodní názvy domén (IDN) 2.0 SP1.</span><span class="sxs-lookup"><span data-stu-id="72091-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="72091-125">Aktuální uživatelé neuvidí žádné chování se liší od rozhraní .NET Framework 2.0, pokud konkrétně povolit IRI a IDN podporovat.</span><span class="sxs-lookup"><span data-stu-id="72091-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="72091-126">Tím se zajistí kompatibilitu aplikace s předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72091-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="72091-127">Povolení podpory pro IRI, je potřeba udělat následující dvě změny:</span><span class="sxs-lookup"><span data-stu-id="72091-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="72091-128">Přidejte následující řádek do souboru machine.config v adresáři rozhraní .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="72091-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="72091-129">Zadejte, zda má, analýza mezinárodní název domény (IDN) použít na název domény a zda má být použita IRI Analýza pravidla.</span><span class="sxs-lookup"><span data-stu-id="72091-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="72091-130">To lze provést v souboru machine.config nebo v souboru app.config.</span><span class="sxs-lookup"><span data-stu-id="72091-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="72091-131">Existují tři možné hodnoty pro IDN v závislosti na servery DNS, které se používají:</span><span class="sxs-lookup"><span data-stu-id="72091-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="72091-132">IDN, povoleno = All</span><span class="sxs-lookup"><span data-stu-id="72091-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="72091-133">Tato hodnota převede názvy domén, Unicode jejich ekvivalenty Punycode (IDN. názvy).</span><span class="sxs-lookup"><span data-stu-id="72091-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="72091-134">IDN, povoleno = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="72091-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="72091-135">Tato hodnota se převést všechny názvy domén Unicode není v místním intranetu používat kódování Punycode ekvivalenty (IDN. názvy).</span><span class="sxs-lookup"><span data-stu-id="72091-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="72091-136">V takovém případě pro zpracování mezinárodních názvů na místní Intranet, servery DNS, které se používají pro intranetové by měly podporovat překlad kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="72091-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="72091-137">IDN, povoleno = None</span><span class="sxs-lookup"><span data-stu-id="72091-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="72091-138">Tato hodnota nebude převést názvy domén Unicode používat kódování Punycode.</span><span class="sxs-lookup"><span data-stu-id="72091-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="72091-139">Toto je výchozí hodnota, která je konzistentní s chování rozhraní .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="72091-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="72091-140">Povolení IDN převede všechny popisky kódování Unicode v názvu domény jejich ekvivalenty u Punycode.</span><span class="sxs-lookup"><span data-stu-id="72091-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="72091-141">Názvy Punycode obsahovat pouze znaky ASCII a vždy začínají předponou xn –.</span><span class="sxs-lookup"><span data-stu-id="72091-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="72091-142">Důvodem je podpora existující servery DNS na Internetu, protože většina servery DNS podporují pouze znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="72091-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="72091-143">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="72091-143">Configuration Files</span></span>  
 <span data-ttu-id="72091-144">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="72091-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72091-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="72091-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="72091-146">Popis</span><span class="sxs-lookup"><span data-stu-id="72091-146">Description</span></span>  
 <span data-ttu-id="72091-147">Následující příklad ukazuje konfigurace používané <xref:System.Uri> třídy pro podporu analýzy IRI a IDN. názvy.</span><span class="sxs-lookup"><span data-stu-id="72091-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="72091-148">Kód</span><span class="sxs-lookup"><span data-stu-id="72091-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="72091-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="72091-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="72091-150">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="72091-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
