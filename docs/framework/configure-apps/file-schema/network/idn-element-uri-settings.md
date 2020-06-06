---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698161"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="44435-102">\<idn> – element (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="44435-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="44435-103">Určuje, jestli se má pro název domény použít analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="44435-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**  
  
## <a name="syntax"></a><span data-ttu-id="44435-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44435-104">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44435-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44435-105">Attributes and Elements</span></span>  
 <span data-ttu-id="44435-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44435-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44435-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="44435-107">Attributes</span></span>  

|<span data-ttu-id="44435-108">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="44435-108">**Element**</span></span>|<span data-ttu-id="44435-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="44435-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="44435-110">Určuje, jestli se pro název domény použije analýza v mezinárodní doméně (IDN). výchozí hodnota je None.</span><span class="sxs-lookup"><span data-stu-id="44435-110">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="44435-111">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="44435-111">Child elements</span></span>

<span data-ttu-id="44435-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="44435-112">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="44435-113">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="44435-113">Parent elements</span></span>

|<span data-ttu-id="44435-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="44435-114">**Element**</span></span>|<span data-ttu-id="44435-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="44435-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="44435-116">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="44435-116">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="44435-117">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="44435-117">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="44435-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44435-118">Remarks</span></span>

<span data-ttu-id="44435-119">Existující <xref:System.Uri> Třída se rozšířila v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="44435-119">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="44435-120">3,0 SP1 a 2,0 SP1 s podporou pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="44435-120">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="44435-121">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="44435-121">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="44435-122">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44435-122">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="44435-123">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="44435-123">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="44435-124">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="44435-124">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="44435-125">Určete, jestli se má pro název domény použít analýza v mezinárodní doméně (IDN) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="44435-125">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="44435-126">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="44435-126">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="44435-127">Existují tři možné hodnoty pro IDN v závislosti na používaných serverech DNS:</span><span class="sxs-lookup"><span data-stu-id="44435-127">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="44435-128">IDN povolené = vše</span><span class="sxs-lookup"><span data-stu-id="44435-128">idn enabled = All</span></span>  

     <span data-ttu-id="44435-129">Tato hodnota převede všechny názvy domén Unicode na jejich ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="44435-129">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="44435-130">povolené IDN = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="44435-130">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="44435-131">Tato hodnota převede všechny názvy domén Unicode, které nejsou v místním intranetu, aby používaly ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="44435-131">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="44435-132">V tomto případě by se měly servery DNS, které se používají pro intranet, podporovat rozlišení názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="44435-132">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="44435-133">povoleno IDN = None</span><span class="sxs-lookup"><span data-stu-id="44435-133">idn enabled = None</span></span>

     <span data-ttu-id="44435-134">Tato hodnota nepřevede žádné názvy domén Unicode tak, aby používaly Punycode.</span><span class="sxs-lookup"><span data-stu-id="44435-134">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="44435-135">Toto je výchozí hodnota, která je konzistentní s chováním .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="44435-135">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="44435-136">Povolením IDN převedete všechny jmenovky Unicode v názvu domény na jejich ekvivalenty Punycode.</span><span class="sxs-lookup"><span data-stu-id="44435-136">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="44435-137">Názvy Punycode obsahují pouze znaky ASCII a vždy začínají předponou Xn---prefix.</span><span class="sxs-lookup"><span data-stu-id="44435-137">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="44435-138">Důvodem je podpora stávajících serverů DNS na internetu, protože většina serverů DNS podporuje jenom znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="44435-138">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="44435-139">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="44435-139">Configuration files</span></span>

<span data-ttu-id="44435-140">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="44435-140">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="44435-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="44435-141">Example</span></span>

<span data-ttu-id="44435-142">Následující příklad ukazuje konfiguraci, kterou <xref:System.Uri> Třída používá pro podporu IRIch analýz a názvů IDN:</span><span class="sxs-lookup"><span data-stu-id="44435-142">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="44435-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="44435-143">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="44435-144">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="44435-144">Network Settings Schema</span></span>](index.md)
