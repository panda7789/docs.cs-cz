---
title: "&lt;gcallowverylargeobjects –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49046c343ef749e597402f7e19a08fe1f2c98ca0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a><span data-ttu-id="fc06e-102">&lt;gcallowverylargeobjects –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="fc06e-102">&lt;gcAllowVeryLargeObjects&gt; Element</span></span>
<span data-ttu-id="fc06e-103">Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="fc06e-103">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>  
  
 <span data-ttu-id="fc06e-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="fc06e-104">\<configuration> Element</span></span>  
<span data-ttu-id="fc06e-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="fc06e-105">\<runtime> Element</span></span>  
<span data-ttu-id="fc06e-106">\<gcallowverylargeobjects – > elementu</span><span class="sxs-lookup"><span data-stu-id="fc06e-106">\<gcAllowVeryLargeObjects> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc06e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc06e-107">Syntax</span></span>  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc06e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fc06e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fc06e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fc06e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc06e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fc06e-110">Attributes</span></span>  
  
|<span data-ttu-id="fc06e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fc06e-111">Attribute</span></span>|<span data-ttu-id="fc06e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fc06e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fc06e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fc06e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fc06e-114">Určuje, zda jsou pole o celkové velikosti větší než 2 GB povolena na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="fc06e-114">Specifies whether arrays that are greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fc06e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="fc06e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fc06e-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fc06e-116">Value</span></span>|<span data-ttu-id="fc06e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fc06e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fc06e-118">Pole o celkové velikosti větší než 2 GB nejsou povolena.</span><span class="sxs-lookup"><span data-stu-id="fc06e-118">Arrays greater than 2 GB in total size are not enabled.</span></span> <span data-ttu-id="fc06e-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="fc06e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fc06e-120">Pole o celkové velikosti větší než 2 GB jsou povolena na 64bitových platformách.</span><span class="sxs-lookup"><span data-stu-id="fc06e-120">Arrays greater than 2 GB in total size are enabled on 64-bit platforms.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc06e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fc06e-121">Child Elements</span></span>  
 <span data-ttu-id="fc06e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="fc06e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fc06e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fc06e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fc06e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="fc06e-124">Element</span></span>|<span data-ttu-id="fc06e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="fc06e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fc06e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc06e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fc06e-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fc06e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc06e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc06e-128">Remarks</span></span>  
 <span data-ttu-id="fc06e-129">Použití tohoto prvku v konfiguračním souboru aplikace umožňuje použití polí, která jsou větší než 2 GB, ale nedojde ke změně jiných omezení velikosti objektu nebo velikosti pole:</span><span class="sxs-lookup"><span data-stu-id="fc06e-129">Using this element in your application configuration file enables arrays that are larger than 2 GB in size, but does not change other limits on object size or array size:</span></span>  
  
-   <span data-ttu-id="fc06e-130">Maximální počet prvků v poli je <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fc06e-130">The maximum number of elements in an array is <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="fc06e-131">Maximální index v jakémkoli jednom rozměru je 2 147 483 591 (0x7FFFFFC7) pro bajtová pole a pole jednobajtových struktur a 2 146 435 071 (0X7FEFFFFF) pro ostatní typy.</span><span class="sxs-lookup"><span data-stu-id="fc06e-131">The maximum index in any single dimension is 2,147,483,591 (0x7FFFFFC7) for byte arrays and arrays of single-byte structures, and 2,146,435,071 (0X7FEFFFFF) for other types.</span></span>  
  
-   <span data-ttu-id="fc06e-132">Maximální velikost řetězců a dalších objektů mimo pole se nezmění.</span><span class="sxs-lookup"><span data-stu-id="fc06e-132">The maximum size for strings and other non-array objects is unchanged.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fc06e-133">Před zapnutím této funkce je třeba se ujistit, že aplikace neobsahuje nebezpečný kód, což předpokládá, že jsou všechna pole menší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="fc06e-133">Before enabling this feature, ensure that your application does not include unsafe code that assumes that all arrays are smaller than 2 GB in size.</span></span> <span data-ttu-id="fc06e-134">Například nebezpečný kód, který používá pole jako vyrovnávací paměť, může být náchylný k přetečení zásobníku, pokud se při jeho psaní vycházelo z předpokladu, že pole nebude větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="fc06e-134">For example, unsafe code that uses arrays as buffers might be susceptible to buffer overruns if it is written on the assumption that arrays will not exceed 2 GB.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc06e-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc06e-135">Example</span></span>  
 <span data-ttu-id="fc06e-136">Následující příklad ukazuje, jak tuto funkci pro aplikaci povolit.</span><span class="sxs-lookup"><span data-stu-id="fc06e-136">The following example shows how to enable this feature for an application.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc06e-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc06e-137">See Also</span></span>  
 [<span data-ttu-id="fc06e-138">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="fc06e-138">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fc06e-139">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fc06e-139">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
