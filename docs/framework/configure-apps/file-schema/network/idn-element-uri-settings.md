---
title: <idn> – element (nastavení URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698161"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="6ed40-102">@no__t – element > 0idn (nastavení URI)</span><span class="sxs-lookup"><span data-stu-id="6ed40-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="6ed40-103">Určuje, jestli se má pro název domény použít analýza v mezinárodním názvu domény (IDN).</span><span class="sxs-lookup"><span data-stu-id="6ed40-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[<span data-ttu-id="6ed40-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="6ed40-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6ed40-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6ed40-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="6ed40-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<idn >**</span><span class="sxs-lookup"><span data-stu-id="6ed40-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ed40-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ed40-107">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ed40-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ed40-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6ed40-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ed40-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ed40-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ed40-110">Attributes</span></span>  

|<span data-ttu-id="6ed40-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="6ed40-111">**Element**</span></span>|<span data-ttu-id="6ed40-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6ed40-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="6ed40-113">Určuje, jestli se pro název domény použije analýza v mezinárodní doméně (IDN). výchozí hodnota je None.</span><span class="sxs-lookup"><span data-stu-id="6ed40-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="6ed40-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6ed40-114">Child elements</span></span>

<span data-ttu-id="6ed40-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ed40-115">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="6ed40-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6ed40-116">Parent elements</span></span>

|<span data-ttu-id="6ed40-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="6ed40-117">**Element**</span></span>|<span data-ttu-id="6ed40-118">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6ed40-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6ed40-119">identifikátor URI</span><span class="sxs-lookup"><span data-stu-id="6ed40-119">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="6ed40-120">Obsahuje nastavení, která určují, jak .NET Framework zpracovává webové adresy vyjádřené pomocí identifikátorů URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="6ed40-120">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="6ed40-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ed40-121">Remarks</span></span>

<span data-ttu-id="6ed40-122">Existující třída <xref:System.Uri> byla rozšířena v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="6ed40-122">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="6ed40-123">3,0 SP1 a 2,0 SP1 s podporou pro mezinárodní identifikátory prostředků (IRI) a mezinárodní názvy domén (IDN).</span><span class="sxs-lookup"><span data-stu-id="6ed40-123">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="6ed40-124">Stávajícím uživatelům se nezobrazí žádná změna v .NET Framework 2,0, pokud výslovně nepovolí podporu IRI a IDN.</span><span class="sxs-lookup"><span data-stu-id="6ed40-124">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="6ed40-125">Tím zajistíte kompatibilitu aplikace s předchozími verzemi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6ed40-125">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="6ed40-126">Pokud chcete povolit podporu pro IRI, vyžadují se tyto dvě změny:</span><span class="sxs-lookup"><span data-stu-id="6ed40-126">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="6ed40-127">Přidejte následující řádek do souboru Machine. config v adresáři .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="6ed40-127">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="6ed40-128">Určete, jestli se má pro název domény použít analýza v mezinárodní doméně (IDN) a jestli se mají použít pravidla analýzy IRI.</span><span class="sxs-lookup"><span data-stu-id="6ed40-128">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="6ed40-129">To lze provést v souboru Machine. config nebo v souboru App. config.</span><span class="sxs-lookup"><span data-stu-id="6ed40-129">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="6ed40-130">Existují tři možné hodnoty pro IDN v závislosti na používaných serverech DNS:</span><span class="sxs-lookup"><span data-stu-id="6ed40-130">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="6ed40-131">IDN povolené = vše</span><span class="sxs-lookup"><span data-stu-id="6ed40-131">idn enabled = All</span></span>  

     <span data-ttu-id="6ed40-132">Tato hodnota převede všechny názvy domén Unicode na jejich ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="6ed40-132">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="6ed40-133">povolené IDN = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="6ed40-133">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="6ed40-134">Tato hodnota převede všechny názvy domén Unicode, které nejsou v místním intranetu, aby používaly ekvivalenty Punycode (názvy IDN).</span><span class="sxs-lookup"><span data-stu-id="6ed40-134">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="6ed40-135">V tomto případě by se měly servery DNS, které se používají pro intranet, podporovat rozlišení názvů Unicode.</span><span class="sxs-lookup"><span data-stu-id="6ed40-135">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="6ed40-136">povoleno IDN = None</span><span class="sxs-lookup"><span data-stu-id="6ed40-136">idn enabled = None</span></span>

     <span data-ttu-id="6ed40-137">Tato hodnota nepřevede žádné názvy domén Unicode tak, aby používaly Punycode.</span><span class="sxs-lookup"><span data-stu-id="6ed40-137">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="6ed40-138">Toto je výchozí hodnota, která je konzistentní s chováním .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="6ed40-138">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="6ed40-139">Povolením IDN převedete všechny jmenovky Unicode v názvu domény na jejich ekvivalenty Punycode.</span><span class="sxs-lookup"><span data-stu-id="6ed40-139">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="6ed40-140">Názvy Punycode obsahují pouze znaky ASCII a vždy začínají předponou Xn---prefix.</span><span class="sxs-lookup"><span data-stu-id="6ed40-140">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="6ed40-141">Důvodem je podpora stávajících serverů DNS na internetu, protože většina serverů DNS podporuje jenom znaky ASCII (viz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="6ed40-141">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="6ed40-142">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="6ed40-142">Configuration files</span></span>

<span data-ttu-id="6ed40-143">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6ed40-143">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="6ed40-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ed40-144">Example</span></span>

<span data-ttu-id="6ed40-145">Následující příklad ukazuje konfiguraci, kterou používá třída <xref:System.Uri> pro podporu analýzy IRI a názvů IDN:</span><span class="sxs-lookup"><span data-stu-id="6ed40-145">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6ed40-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ed40-146">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="6ed40-147">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="6ed40-147">Network Settings Schema</span></span>](index.md)
