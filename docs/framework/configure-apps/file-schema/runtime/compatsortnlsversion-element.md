---
title: '&lt;CompatSortNLSVersion&gt; Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a40a9e7ad5eb0b6e978054b5e7edcf35e53c42c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578504"
---
# <a name="ltcompatsortnlsversiongt-element"></a><span data-ttu-id="2899d-102">&lt;CompatSortNLSVersion&gt; Element</span><span class="sxs-lookup"><span data-stu-id="2899d-102">&lt;CompatSortNLSVersion&gt; Element</span></span>
<span data-ttu-id="2899d-103">Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="2899d-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="2899d-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2899d-104">\<configuration></span></span>  
<span data-ttu-id="2899d-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="2899d-105">\<runtime></span></span>  
<span data-ttu-id="2899d-106">\<CompatSortNLSVersion > – Element</span><span class="sxs-lookup"><span data-stu-id="2899d-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2899d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2899d-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2899d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2899d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2899d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2899d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2899d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2899d-110">Attributes</span></span>  
  
|<span data-ttu-id="2899d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2899d-111">Attribute</span></span>|<span data-ttu-id="2899d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2899d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2899d-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2899d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2899d-114">Určuje ID národního prostředí, jehož pořadí řazení se má použít.</span><span class="sxs-lookup"><span data-stu-id="2899d-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2899d-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2899d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2899d-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2899d-116">Value</span></span>|<span data-ttu-id="2899d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2899d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2899d-118">4096</span><span class="sxs-lookup"><span data-stu-id="2899d-118">4096</span></span>|<span data-ttu-id="2899d-119">ID národního prostředí, které představuje alternativní pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="2899d-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="2899d-120">V tomto případě hodnota 4096 představuje pořadí řazení [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a starší verze.</span><span class="sxs-lookup"><span data-stu-id="2899d-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2899d-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2899d-121">Child Elements</span></span>  
 <span data-ttu-id="2899d-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2899d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2899d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2899d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2899d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2899d-124">Element</span></span>|<span data-ttu-id="2899d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2899d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2899d-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2899d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2899d-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2899d-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2899d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2899d-128">Remarks</span></span>  
 <span data-ttu-id="2899d-129">Protože porovnání řetězců, řazení a operace velikosti písmen provádět <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> třídy v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] v souladu s standardem Unicode 5.1, výsledky metod porovnání řetězců, jako <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> může lišit od předchozí verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2899d-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="2899d-130">Pokud vaše aplikace závisí na chování starších verzí, můžete obnovit porovnání řetězců a pravidla řazení používaná v [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] a předchozích verzích přidáním `<CompatSortNLSVersion>` prvku v konfiguračním souboru vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2899d-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2899d-131">Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="2899d-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="2899d-132">Také vám pomůže starší pravidla řazení a porovnání ve specifické aplikační doméně předáním řetězce "NetFx40_Legacy20SortingBehavior" <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metoda při vytváření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2899d-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2899d-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="2899d-133">Example</span></span>  
 <span data-ttu-id="2899d-134">Následující příklad vytvoří dvě <xref:System.String> a volá <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu pro jejich porovnání pomocí konvencí aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="2899d-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="2899d-135">Při spuštění v příkladu [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="2899d-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="2899d-136">Toto je zcela liší od výstupu, který se zobrazí, pokud příklad spustíte ve [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2899d-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="2899d-137">Pokud ale přidáte následující konfigurační soubor v příkladu adresáře a poté příklad spustíte ve [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], výstup je stejný jako, který v příkladu vytvořen při spuštění [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2899d-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2899d-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2899d-138">See also</span></span>
- [<span data-ttu-id="2899d-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2899d-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="2899d-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2899d-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
