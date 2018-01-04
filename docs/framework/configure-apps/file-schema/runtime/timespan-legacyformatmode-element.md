---
title: "&lt;Timespan_legacyformatmode –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be4b26cdc79cef0854221172b8dea0bcc0f50981
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttimespanlegacyformatmodegt-element"></a><span data-ttu-id="5549d-102">&lt;Timespan_legacyformatmode –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="5549d-102">&lt;TimeSpan_LegacyFormatMode&gt; Element</span></span>
<span data-ttu-id="5549d-103">Určuje, zda modul runtime zachovává starší verze chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5549d-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="5549d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5549d-104">\<configuration></span></span>  
<span data-ttu-id="5549d-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="5549d-105">\<runtime></span></span>  
<span data-ttu-id="5549d-106">< timespan_legacyformatmode – ></span><span class="sxs-lookup"><span data-stu-id="5549d-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5549d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5549d-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5549d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5549d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5549d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5549d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5549d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5549d-110">Attributes</span></span>  
  
|<span data-ttu-id="5549d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5549d-111">Attribute</span></span>|<span data-ttu-id="5549d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5549d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5549d-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5549d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5549d-114">Určuje, zda modul runtime používá starší verze formátování chování s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5549d-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5549d-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="5549d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5549d-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5549d-116">Value</span></span>|<span data-ttu-id="5549d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5549d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5549d-118">Modul runtime neobnoví starší verze formátování chování.</span><span class="sxs-lookup"><span data-stu-id="5549d-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="5549d-119">Modul runtime obnoví starší verze formátování chování.</span><span class="sxs-lookup"><span data-stu-id="5549d-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5549d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5549d-120">Child Elements</span></span>  
 <span data-ttu-id="5549d-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="5549d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5549d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5549d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5549d-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="5549d-123">Element</span></span>|<span data-ttu-id="5549d-124">Popis</span><span class="sxs-lookup"><span data-stu-id="5549d-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5549d-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5549d-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5549d-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="5549d-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5549d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5549d-127">Remarks</span></span>  
 <span data-ttu-id="5549d-128">Od verze [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> rozhraní a podporuje formátování operace s řetězci standardní a vlastní formát.</span><span class="sxs-lookup"><span data-stu-id="5549d-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="5549d-129">Pokud metoda analýzy zaznamená řetězce formátu nebo nepodporovaný formát specifikátor, vyvolá výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5549d-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5549d-130">V předchozích verzích rozhraní .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporoval řetězce formátu.</span><span class="sxs-lookup"><span data-stu-id="5549d-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="5549d-131">Ale celá řada vývojářů omylem předpokládá se, že <xref:System.TimeSpan> podporovat sadu řetězce formátu a použít je v [složené formátování operations](../../../../../docs/standard/base-types/composite-formatting.md) s metodami, jako <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5549d-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5549d-132">Normálně Pokud typ implementuje <xref:System.IFormattable> a podporuje formátování řetězce, volání metodě formátování s nepodporovaný formát řetězce obvykle throw <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5549d-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="5549d-133">Ale protože <xref:System.TimeSpan> neimplementovala <xref:System.IFormattable>, modul runtime ignorovat řetězec formátu a místo toho volat <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="5549d-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5549d-134">To znamená, že i když řetězce formátu nemělo žádný vliv na operace formátování, jejich přítomnosti nevedly <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="5549d-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5549d-135">Pro případy, ve kterých starší kód předá složeného formátování metoda a neplatný formát řetězce a tento kód nemůže být překompilovat, můžete použít `<TimeSpan_LegacyFormatMode>` elementu, který chcete obnovit starší verze <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="5549d-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="5549d-136">Když nastavíte `enabled` tohoto prvku do atribut `true`, složené formátování metoda výsledkem volání <xref:System.TimeSpan.ToString?displayProperty=nameWithType> místo <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="5549d-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5549d-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="5549d-137">Example</span></span>  
 <span data-ttu-id="5549d-138">Následující příklad vytvoří <xref:System.TimeSpan> objekt a pokusy o naformátujte ho s <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metoda pomocí Nepodporovaný standardní formát řetězce.</span><span class="sxs-lookup"><span data-stu-id="5549d-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="5549d-139">Při spuštění v příkladu [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] nebo ve starší verzi, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="5549d-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="5549d-140">To zřetelně liší z výstupu Pokud spustíte v příkladu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze:</span><span class="sxs-lookup"><span data-stu-id="5549d-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="5549d-141">Ale pokud přidáte následujícího konfiguračního souboru v příkladu je adresáře a spusťte v příkladu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze je stejná jako vyprodukované v příkladu, když se spustí na výstup [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5549d-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5549d-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="5549d-142">See Also</span></span>  
 [<span data-ttu-id="5549d-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="5549d-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="5549d-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5549d-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
