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
ms.openlocfilehash: f13265e2056c8eca62cd510154dd7c096eeabb00
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117684"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="13f8b-102">\<element > CompatSortNLSVersion</span><span class="sxs-lookup"><span data-stu-id="13f8b-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="13f8b-103">Určuje, zda by modul runtime měl při porovnávání řetězců použít starší pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="13f8b-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
<span data-ttu-id="13f8b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="13f8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13f8b-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="13f8b-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="13f8b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion >**</span><span class="sxs-lookup"><span data-stu-id="13f8b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13f8b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13f8b-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13f8b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13f8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="13f8b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13f8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13f8b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="13f8b-110">Attributes</span></span>  
  
|<span data-ttu-id="13f8b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="13f8b-111">Attribute</span></span>|<span data-ttu-id="13f8b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="13f8b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="13f8b-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="13f8b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="13f8b-114">Určuje ID národního prostředí, jehož pořadí řazení se má použít.</span><span class="sxs-lookup"><span data-stu-id="13f8b-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="13f8b-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="13f8b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="13f8b-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="13f8b-116">Value</span></span>|<span data-ttu-id="13f8b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="13f8b-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13f8b-118">4096</span><span class="sxs-lookup"><span data-stu-id="13f8b-118">4096</span></span>|<span data-ttu-id="13f8b-119">ID národního prostředí, které představuje alternativní pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="13f8b-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="13f8b-120">V tomto případě 4096 představuje pořadí řazení .NET Framework 3,5 a starších verzí.</span><span class="sxs-lookup"><span data-stu-id="13f8b-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13f8b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13f8b-121">Child Elements</span></span>  
 <span data-ttu-id="13f8b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="13f8b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13f8b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13f8b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="13f8b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="13f8b-124">Element</span></span>|<span data-ttu-id="13f8b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="13f8b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="13f8b-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13f8b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="13f8b-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="13f8b-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13f8b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13f8b-128">Remarks</span></span>  
 <span data-ttu-id="13f8b-129">Vzhledem k tomu, že porovnání řetězců, řazení a operace s velkými a malými písmeny prováděné třídou <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> v .NET Framework 4 odpovídají standardu Unicode 5,1, výsledky metod porovnání řetězců, jako je <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>, se mohou lišit od předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="13f8b-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="13f8b-130">Pokud vaše aplikace závisí na starším chování, můžete obnovit pravidla porovnání a řazení řetězců používané v .NET Framework 3,5 a starších verzích zahrnutím prvku `<CompatSortNLSVersion>` do konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="13f8b-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="13f8b-131">Obnovení starších pravidel porovnání a řazení řetězců vyžaduje, aby v místním systému byla k dispozici dynamická knihovna sort00001000.dll.</span><span class="sxs-lookup"><span data-stu-id="13f8b-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="13f8b-132">Můžete také použít starší řazení řetězců a pravidla porovnávání v konkrétní aplikační doméně předáním řetězce "NetFx40_Legacy20SortingBehavior" do metody <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> při vytváření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="13f8b-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13f8b-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="13f8b-133">Example</span></span>  
 <span data-ttu-id="13f8b-134">Následující příklad vytvoří instanci dvou objektů <xref:System.String> a zavolá metodu <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> pro porovnání pomocí konvencí aktuální jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="13f8b-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="13f8b-135">Když spustíte příklad na .NET Framework 4, zobrazí se následující výstup.</span><span class="sxs-lookup"><span data-stu-id="13f8b-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="13f8b-136">To se zcela liší od výstupu, který se zobrazí při spuštění příkladu na .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="13f8b-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="13f8b-137">Pokud však do adresáře s příkladem přidáte následující konfigurační soubor a poté spustíte příklad na .NET Framework 4, výstup je stejný jako v příkladu, který byl vytvořen v příkladu při spuštění v .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="13f8b-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13f8b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13f8b-138">See also</span></span>

- [<span data-ttu-id="13f8b-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="13f8b-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="13f8b-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="13f8b-140">Configuration File Schema</span></span>](../index.md)
