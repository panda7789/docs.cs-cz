---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698092"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="42c11-102">\<element > iriParsing (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="42c11-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="42c11-103">Určuje, jestli se má u <xref:System.Uri> použít analýza mezinárodního identifikátoru prostředků (IRI) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="42c11-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="42c11-104">**Konfigurace \<>** </span><span class="sxs-lookup"><span data-stu-id="42c11-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="42c11-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="42c11-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="42c11-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<iriParsing >**</span><span class="sxs-lookup"><span data-stu-id="42c11-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c11-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c11-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42c11-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="42c11-108">Attributes and Elements</span></span>  
 <span data-ttu-id="42c11-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="42c11-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42c11-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="42c11-110">Attributes</span></span>  
  
|<span data-ttu-id="42c11-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="42c11-111">**Element**</span></span>|<span data-ttu-id="42c11-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="42c11-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="42c11-113">Určuje, zda je povolena analýza IRI.</span><span class="sxs-lookup"><span data-stu-id="42c11-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="42c11-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="42c11-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42c11-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="42c11-115">Child Elements</span></span>  
 <span data-ttu-id="42c11-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="42c11-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42c11-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="42c11-117">Parent Elements</span></span>  
  
|<span data-ttu-id="42c11-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="42c11-118">**Element**</span></span>|<span data-ttu-id="42c11-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="42c11-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="42c11-120">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="42c11-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="42c11-121">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="42c11-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42c11-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42c11-122">Remarks</span></span>  
 <span data-ttu-id="42c11-123">Existující třída <xref:System.Uri> byla rozšířena v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="42c11-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="42c11-124">3,0 SP1 a 2,0 SP1 pro poskytování podpory pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="42c11-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="42c11-125">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="42c11-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="42c11-126">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42c11-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="42c11-127">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="42c11-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="42c11-128">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="42c11-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="42c11-129">Určete, jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="42c11-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="42c11-130">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="42c11-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="42c11-131">Povolení analýzy IRI (iriParsing Enabled = `true`) provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="42c11-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="42c11-132">Výchozí hodnota je `false` a provede normalizaci a kontrolu znaku podle RFC 2396 a RFC 3986 (pro literály IPv6).</span><span class="sxs-lookup"><span data-stu-id="42c11-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="42c11-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="42c11-133">Configuration Files</span></span>  
 <span data-ttu-id="42c11-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="42c11-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c11-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="42c11-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="42c11-136">Popis</span><span class="sxs-lookup"><span data-stu-id="42c11-136">Description</span></span>  
 <span data-ttu-id="42c11-137">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="42c11-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="42c11-138">Kód</span><span class="sxs-lookup"><span data-stu-id="42c11-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42c11-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42c11-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="42c11-140">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="42c11-140">Network Settings Schema</span></span>](index.md)
