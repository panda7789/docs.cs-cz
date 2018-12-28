---
title: '&lt;Timespan_legacyformatmode –&gt; – Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e371f45286c88c9136b869e750009dadeb261877
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612254"
---
# <a name="lttimespanlegacyformatmodegt-element"></a><span data-ttu-id="7574f-102">&lt;Timespan_legacyformatmode –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="7574f-102">&lt;TimeSpan_LegacyFormatMode&gt; Element</span></span>
<span data-ttu-id="7574f-103">Určuje, zda modul runtime zachová starší chování při formátování operací s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7574f-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="7574f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="7574f-104">\<configuration></span></span>  
<span data-ttu-id="7574f-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="7574f-105">\<runtime></span></span>  
<span data-ttu-id="7574f-106">< timespan_legacyformatmode – ></span><span class="sxs-lookup"><span data-stu-id="7574f-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7574f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7574f-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7574f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7574f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7574f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7574f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7574f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7574f-110">Attributes</span></span>  
  
|<span data-ttu-id="7574f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7574f-111">Attribute</span></span>|<span data-ttu-id="7574f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7574f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7574f-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7574f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7574f-114">Určuje, zda modul runtime používá starší verzi chování při formátování s <xref:System.TimeSpan?displayProperty=nameWithType> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7574f-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7574f-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="7574f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7574f-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7574f-116">Value</span></span>|<span data-ttu-id="7574f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7574f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7574f-118">Modul runtime neobnoví starší chování při formátování.</span><span class="sxs-lookup"><span data-stu-id="7574f-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="7574f-119">Modul runtime obnoví starší chování při formátování.</span><span class="sxs-lookup"><span data-stu-id="7574f-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7574f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7574f-120">Child Elements</span></span>  
 <span data-ttu-id="7574f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="7574f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7574f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7574f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7574f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="7574f-123">Element</span></span>|<span data-ttu-id="7574f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="7574f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7574f-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7574f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7574f-126">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7574f-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7574f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7574f-127">Remarks</span></span>  
 <span data-ttu-id="7574f-128">Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], <xref:System.TimeSpan?displayProperty=nameWithType> struktury implementuje <xref:System.IFormattable> rozhraní a podporuje formátování operací pomocí standardních a vlastních formátovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="7574f-128">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="7574f-129">Pokud metoda analýzy se zaznamená řetězce formátu nebo nepodporovaný formát specifikátoru, vyvolá výjimku <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="7574f-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="7574f-130">V předchozích verzích rozhraní .NET Framework <xref:System.TimeSpan> struktura neimplementovala <xref:System.IFormattable> a nepodporovalo formátovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="7574f-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="7574f-131">Nicméně mnoho vývojářů omylem předpokládá se, že <xref:System.TimeSpan> podporoval množinu řetězců formátu a používat je v [složeného formátování operace](../../../../../docs/standard/base-types/composite-formatting.md) s metodami, jako <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7574f-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7574f-132">Obvykle Pokud typ implementuje <xref:System.IFormattable> a podporuje formátovací řetězce, volání metody se nepodporovaný formát pro formátování řetězce obvykle vyvolat <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="7574f-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="7574f-133">Ale protože <xref:System.TimeSpan> neimplementovala <xref:System.IFormattable>, modul runtime ignorovat formátovací řetězec a místo toho volat <xref:System.TimeSpan.ToString?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="7574f-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7574f-134">To znamená, že i když formátovací řetězce nemělo žádný vliv na operace formátování, jejich přítomnost nezpůsobil ztrátu v <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="7574f-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="7574f-135">Pro případy, ve kterých starší kód předá složeného formátování metoda a neplatný řetězec formátu a nemůže být překompilovány tento kód, můžete použít `<TimeSpan_LegacyFormatMode>` prvek, který chcete obnovit starší <xref:System.TimeSpan> chování.</span><span class="sxs-lookup"><span data-stu-id="7574f-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="7574f-136">Při nastavení `enabled` atribut tohoto elementu `true`, složeného formátování výsledky metody při volání k <xref:System.TimeSpan.ToString?displayProperty=nameWithType> spíše než <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>a <xref:System.FormatException> není vyvolána.</span><span class="sxs-lookup"><span data-stu-id="7574f-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7574f-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="7574f-137">Example</span></span>  
 <span data-ttu-id="7574f-138">Následující příklad vytvoří <xref:System.TimeSpan> objektu a pokusí se ho naformátovat <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> metoda pomocí nepodporované standardní formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="7574f-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="7574f-139">Při spuštění v příkladu [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] nebo s dřívější verzí, se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="7574f-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="7574f-140">Tím se liší je výrazně z výstupu pokud příklad spustíte ve [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verzi:</span><span class="sxs-lookup"><span data-stu-id="7574f-140">This differs markedly from the output if you run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="7574f-141">Pokud ale přidáte následující konfigurační soubor v příkladu adresáře a poté příklad spustíte ve [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] nebo novější verze, výstup je stejný jako, který v příkladu vytvořen při spuštění [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7574f-141">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7574f-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="7574f-142">See Also</span></span>  
- [<span data-ttu-id="7574f-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="7574f-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="7574f-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7574f-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
