---
title: Element <CompatSortNLSVersion>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154267"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="f5cbd-102">Element \<CompatSortNLSVersion></span><span class="sxs-lookup"><span data-stu-id="f5cbd-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="f5cbd-103">Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="f5cbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5cbd-104">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f5cbd-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f5cbd-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f5cbd-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f5cbd-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f5cbd-107">Attributes</span></span>  
  
|<span data-ttu-id="f5cbd-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f5cbd-108">Attribute</span></span>|<span data-ttu-id="f5cbd-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f5cbd-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f5cbd-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f5cbd-111">Určuje ID národního prostředí, jehož pořadí řazení se má použít.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-111">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f5cbd-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="f5cbd-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="f5cbd-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f5cbd-113">Value</span></span>|<span data-ttu-id="f5cbd-114">Description</span><span class="sxs-lookup"><span data-stu-id="f5cbd-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f5cbd-115">4 096</span><span class="sxs-lookup"><span data-stu-id="f5cbd-115">4096</span></span>|<span data-ttu-id="f5cbd-116">ID národního prostředí, které představuje alternativní pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-116">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="f5cbd-117">V tomto případě 4096 představuje pořadí řazení .NET Framework 3,5 a starších verzí.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-117">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f5cbd-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f5cbd-118">Child Elements</span></span>  
 <span data-ttu-id="f5cbd-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="f5cbd-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f5cbd-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f5cbd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f5cbd-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="f5cbd-121">Element</span></span>|<span data-ttu-id="f5cbd-122">Description</span><span class="sxs-lookup"><span data-stu-id="f5cbd-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f5cbd-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f5cbd-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5cbd-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5cbd-125">Remarks</span></span>  
 <span data-ttu-id="f5cbd-126">Vzhledem k tomu, že porovnání řetězců, řazení a operace s velkými a malými písmeny prováděné <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> třídou v .NET Framework 4 odpovídají standardu Unicode 5,1, výsledky metod porovnání řetězců, jako je <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> a se <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> mohou lišit od předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-126">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="f5cbd-127">Pokud vaše aplikace závisí na starším chování, můžete obnovit pravidla porovnání a řazení řetězců používané v .NET Framework 3,5 a starších verzích zahrnutím `<CompatSortNLSVersion>` elementu do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-127">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5cbd-128">Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-128">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="f5cbd-129">Můžete také použít starší řazení řetězců a pravidla porovnávání v konkrétní aplikační doméně předáním řetězce "NetFx40_Legacy20SortingBehavior" do <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> metody při vytváření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-129">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5cbd-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5cbd-130">Example</span></span>  
 <span data-ttu-id="f5cbd-131">Následující příklad vytvoří instanci dvou <xref:System.String> objektů a zavolá <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metodu pro jejich porovnání pomocí konvencí aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-131">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="f5cbd-132">Když spustíte příklad na .NET Framework 4, zobrazí se následující výstup:</span><span class="sxs-lookup"><span data-stu-id="f5cbd-132">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="f5cbd-133">To se zcela liší od výstupu, který se zobrazí, když spustíte příklad na .NET Framework 3,5:</span><span class="sxs-lookup"><span data-stu-id="f5cbd-133">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="f5cbd-134">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a poté spustíte příklad na .NET Framework 4, výstup je stejný jako v příkladu, který byl vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="f5cbd-134">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5cbd-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5cbd-135">See also</span></span>

- [<span data-ttu-id="f5cbd-136">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="f5cbd-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f5cbd-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f5cbd-137">Configuration File Schema</span></span>](../index.md)
