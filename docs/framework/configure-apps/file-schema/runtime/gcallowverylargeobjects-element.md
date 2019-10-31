---
title: Element <gcAllowVeryLargeObjects>
ms.date: 03/30/2017
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
ms.openlocfilehash: b6230833808ec45d702502e36f929db4e03173e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116795"
---
# <a name="gcallowverylargeobjects-element"></a><span data-ttu-id="55790-102">\<element > gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="55790-102">\<gcAllowVeryLargeObjects> Element</span></span>
<span data-ttu-id="55790-103">Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="55790-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
<span data-ttu-id="55790-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="55790-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55790-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="55790-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="55790-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcAllowVeryLargeObjects >**</span><span class="sxs-lookup"><span data-stu-id="55790-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcAllowVeryLargeObjects>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55790-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55790-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55790-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="55790-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55790-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="55790-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55790-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="55790-110">Attributes</span></span>  
  
|<span data-ttu-id="55790-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="55790-111">Attribute</span></span>|<span data-ttu-id="55790-112">Popis</span><span class="sxs-lookup"><span data-stu-id="55790-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55790-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="55790-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55790-114">Určuje, zda jsou pole o celkové velikosti větší než 2 GB povolena na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="55790-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55790-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="55790-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55790-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="55790-116">Value</span></span>|<span data-ttu-id="55790-117">Popis</span><span class="sxs-lookup"><span data-stu-id="55790-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55790-118">Pole o celkové velikosti větší než 2 GB nejsou povolena.</span><span class="sxs-lookup"><span data-stu-id="55790-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="55790-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="55790-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="55790-120">Pole o celkové velikosti větší než 2 GB jsou povolena na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="55790-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55790-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="55790-121">Child Elements</span></span>  
 <span data-ttu-id="55790-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="55790-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55790-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="55790-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55790-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="55790-124">Element</span></span>|<span data-ttu-id="55790-125">Popis</span><span class="sxs-lookup"><span data-stu-id="55790-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55790-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55790-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55790-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="55790-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55790-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55790-128">Remarks</span></span>  
 <span data-ttu-id="55790-129">Použití tohoto prvku v konfiguračním souboru aplikace umožňuje použití polí, která jsou větší než 2 GB, ale nedojde ke změně jiných omezení velikosti objektu nebo velikosti pole:</span><span class="sxs-lookup"><span data-stu-id="55790-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
- <span data-ttu-id="55790-130">Maximální počet prvků v poli je <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55790-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="55790-131">Maximální index v jakémkoli jednom rozměru je 2 147 483 591 (0x7FFFFFC7) pro bajtová pole a pole jednobajtových struktur a 2 146 435 071 (0X7FEFFFFF) pro ostatní typy.</span><span class="sxs-lookup"><span data-stu-id="55790-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
- <span data-ttu-id="55790-132">Maximální velikost řetězců a dalších objektů mimo pole se nezmění.</span><span class="sxs-lookup"><span data-stu-id="55790-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="55790-133">Před zapnutím této funkce je třeba se ujistit, že aplikace neobsahuje nebezpečný kód, což předpokládá, že jsou všechna pole menší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="55790-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="55790-134">Například nebezpečný kód, který používá pole jako vyrovnávací paměť, může být náchylný k přetečení zásobníku, pokud se při jeho psaní vycházelo z předpokladu, že pole nebude větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="55790-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55790-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="55790-135">Example</span></span>  
 <span data-ttu-id="55790-136">Následující příklad ukazuje, jak tuto funkci pro aplikaci povolit.</span><span class="sxs-lookup"><span data-stu-id="55790-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="supported-in"></a><span data-ttu-id="55790-137">Podporováno v:</span><span class="sxs-lookup"><span data-stu-id="55790-137">Supported in</span></span>

<span data-ttu-id="55790-138">.NET Framework 4,5 a novější verze</span><span class="sxs-lookup"><span data-stu-id="55790-138">.NET Framework 4.5 and later versions</span></span>

## <a name="see-also"></a><span data-ttu-id="55790-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55790-139">See also</span></span>

- [<span data-ttu-id="55790-140">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="55790-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55790-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="55790-141">Configuration File Schema</span></span>](../index.md)
