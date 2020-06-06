---
title: <iriParsing> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698092"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="40e28-102">\<iriParsing> – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="40e28-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="40e28-103">Určuje, jestli se má použít analýza mezinárodní identifikátoru prostředků (IRI) <xref:System.Uri> a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="40e28-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="40e28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40e28-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="40e28-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="40e28-105">Attributes and Elements</span></span>  
 <span data-ttu-id="40e28-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="40e28-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="40e28-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="40e28-107">Attributes</span></span>  
  
|<span data-ttu-id="40e28-108">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="40e28-108">**Element**</span></span>|<span data-ttu-id="40e28-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="40e28-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="40e28-110">Určuje, zda je povolena analýza IRI.</span><span class="sxs-lookup"><span data-stu-id="40e28-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="40e28-111">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="40e28-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="40e28-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="40e28-112">Child Elements</span></span>  
 <span data-ttu-id="40e28-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="40e28-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="40e28-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="40e28-114">Parent Elements</span></span>  
  
|<span data-ttu-id="40e28-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="40e28-115">**Element**</span></span>|<span data-ttu-id="40e28-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="40e28-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="40e28-117">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="40e28-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="40e28-118">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="40e28-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40e28-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40e28-119">Remarks</span></span>  
 <span data-ttu-id="40e28-120">Existující <xref:System.Uri> Třída se rozšířila v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="40e28-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="40e28-121">3,0 SP1 a 2,0 SP1 pro poskytování podpory pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="40e28-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="40e28-122">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="40e28-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="40e28-123">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40e28-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="40e28-124">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="40e28-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="40e28-125">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="40e28-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="40e28-126">Určete, jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="40e28-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="40e28-127">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="40e28-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="40e28-128">Povolení analýzy IRI (iriParsing Enabled = `true` ) provede normalizaci a kontrolu znaku podle nejnovějších pravidel IRI v dokumentu RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="40e28-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="40e28-129">Výchozí hodnota je `false` a provede normalizaci a kontrolu znaku podle rfc 2396 a rfc 3986 (pro literály IPv6).</span><span class="sxs-lookup"><span data-stu-id="40e28-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="40e28-130">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="40e28-130">Configuration Files</span></span>  
 <span data-ttu-id="40e28-131">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="40e28-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="40e28-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="40e28-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="40e28-133">Description</span><span class="sxs-lookup"><span data-stu-id="40e28-133">Description</span></span>  
 <span data-ttu-id="40e28-134">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> Třída používá pro podporu IRIch analýz a názvů IDN.</span><span class="sxs-lookup"><span data-stu-id="40e28-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="40e28-135">Kód</span><span class="sxs-lookup"><span data-stu-id="40e28-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="40e28-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="40e28-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="40e28-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="40e28-137">Network Settings Schema</span></span>](index.md)
