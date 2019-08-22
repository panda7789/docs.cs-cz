---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664089"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="8c0e8-102">\<iriParsing – element > (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="8c0e8-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="8c0e8-103">Určuje, jestli se <xref:System.Uri> má použít analýza mezinárodní identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="8c0e8-104">Hierarchie schématu</span><span class="sxs-lookup"><span data-stu-id="8c0e8-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="8c0e8-105">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="8c0e8-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="8c0e8-106">\<Identifikátor URI > – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="8c0e8-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="8c0e8-107">\<iriParsing></span><span class="sxs-lookup"><span data-stu-id="8c0e8-107">\<iriParsing></span></span>](iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="8c0e8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c0e8-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c0e8-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c0e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8c0e8-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c0e8-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c0e8-111">Attributes</span></span>  
  
|<span data-ttu-id="8c0e8-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-112">**Element**</span></span>|<span data-ttu-id="8c0e8-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="8c0e8-114">Určuje, zda je povolena analýza IRI.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="8c0e8-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c0e8-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c0e8-116">Child Elements</span></span>  
 <span data-ttu-id="8c0e8-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="8c0e8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c0e8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c0e8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8c0e8-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-119">**Element**</span></span>|<span data-ttu-id="8c0e8-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8c0e8-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8c0e8-121">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="8c0e8-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="8c0e8-122">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="8c0e8-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c0e8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c0e8-123">Remarks</span></span>  
 <span data-ttu-id="8c0e8-124">Existující <xref:System.Uri> třída se rozšířila v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="8c0e8-125">3,0 SP1 a 2,0 SP1 pro poskytování podpory pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="8c0e8-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="8c0e8-126">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="8c0e8-127">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="8c0e8-128">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="8c0e8-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="8c0e8-129">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="8c0e8-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="8c0e8-130">Určete, jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="8c0e8-131">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="8c0e8-132">Povolení analýzy IRI (IriParsing Enabled = `true`) provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="8c0e8-133">Výchozí hodnota je `false` a provede normalizaci a kontrolu znaku podle RFC 2396 a RFC 3986 (pro literály IPv6).</span><span class="sxs-lookup"><span data-stu-id="8c0e8-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="8c0e8-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8c0e8-134">Configuration Files</span></span>  
 <span data-ttu-id="8c0e8-135">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8c0e8-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c0e8-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c0e8-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="8c0e8-137">Popis</span><span class="sxs-lookup"><span data-stu-id="8c0e8-137">Description</span></span>  
 <span data-ttu-id="8c0e8-138">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> třída používá pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="8c0e8-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8c0e8-139">Kód</span><span class="sxs-lookup"><span data-stu-id="8c0e8-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c0e8-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c0e8-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="8c0e8-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8c0e8-141">Network Settings Schema</span></span>](index.md)
