---
title: '&lt;UseRandomizedStringHashAlgorithm&gt; – Element'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15a86c1df3e7d6a9d8ddd102bd34aede46c08ba8
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612085"
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a><span data-ttu-id="e5189-102">&lt;UseRandomizedStringHashAlgorithm&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="e5189-102">&lt;UseRandomizedStringHashAlgorithm&gt; Element</span></span>
<span data-ttu-id="e5189-103">Určuje, zda modul common language runtime vypočítá hash kódy pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="e5189-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e5189-104">\<configuration></span></span>  
<span data-ttu-id="e5189-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="e5189-105">\<runtime></span></span>  
<span data-ttu-id="e5189-106">\<UseRandomizedStringHashAlgorithm ></span><span class="sxs-lookup"><span data-stu-id="e5189-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5189-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5189-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5189-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5189-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e5189-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e5189-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5189-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5189-110">Attributes</span></span>  
  
|<span data-ttu-id="e5189-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e5189-111">Attribute</span></span>|<span data-ttu-id="e5189-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e5189-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="e5189-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e5189-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="e5189-114">Určuje, zda kódy hash pro řetězce jsou vypočítány na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e5189-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="e5189-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e5189-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e5189-116">Value</span></span>|<span data-ttu-id="e5189-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e5189-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="e5189-118">Modul common language runtime nepočítá kódy hash pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu řetězce kódů hash.</span><span class="sxs-lookup"><span data-stu-id="e5189-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="e5189-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="e5189-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="e5189-120">Modul common language runtime vypočítá hash kódy pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="e5189-121">Shodné řetězce v různých aplikačních doménách a různých procesech budou mít různé hash kódy.</span><span class="sxs-lookup"><span data-stu-id="e5189-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5189-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5189-122">Child Elements</span></span>  
 <span data-ttu-id="e5189-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="e5189-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5189-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5189-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e5189-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5189-125">Element</span></span>|<span data-ttu-id="e5189-126">Popis</span><span class="sxs-lookup"><span data-stu-id="e5189-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e5189-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5189-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e5189-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e5189-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5189-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5189-129">Remarks</span></span>  
 <span data-ttu-id="e5189-130">Ve výchozím nastavení <xref:System.StringComparer> třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda používat jeden algoritmus hash, který generuje kód hash konzistentně napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="e5189-131">Jedná se o ekvivalent k nastavení `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu `0`.</span><span class="sxs-lookup"><span data-stu-id="e5189-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="e5189-132">To je algoritmus hash, který je používán [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5189-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="e5189-133"><xref:System.StringComparer> Třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metodu můžete použít také jiný algoritmu hash, který vypočítává hash kódy na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="e5189-134">V důsledku toho se kódy hash pro odpovídající řetězce budou lišit napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="e5189-135">To je přihlašovaná funkce; využívat jejich výhod, musíte nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu `1`.</span><span class="sxs-lookup"><span data-stu-id="e5189-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="e5189-136">Vyhledání řetězce v hashovací tabulce je obvykle operace O(1).</span><span class="sxs-lookup"><span data-stu-id="e5189-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="e5189-137">Ale při výskytu velkého počtu kolizí vyhledávání může stát O (n<sup>2</sup>) operace.</span><span class="sxs-lookup"><span data-stu-id="e5189-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="e5189-138">Můžete použít `<UseRandomizedStringHashAlgorithm>` element konfigurace ke generování náhodného algoritmu hash pro doménu aplikace, která zase omezuje počet potenciálních kolizí, zejména pokud klíče, z nichž se počítají hodnoty hash kódů jsou založeny na vstup dat uživatelé.</span><span class="sxs-lookup"><span data-stu-id="e5189-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5189-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5189-139">Example</span></span>  
 <span data-ttu-id="e5189-140">Následující příklad definuje `DisplayString` třídu, která zahrnuje soukromou konstantu řetězce, `s`, jehož hodnota je "Toto je řetězec".</span><span class="sxs-lookup"><span data-stu-id="e5189-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="e5189-141">Zahrnuje také `ShowStringHashCode` metodu, která zobrazí hodnotu řetězce a jeho kód hash spolu s názvem domény aplikace, ve kterém se metoda provádí.</span><span class="sxs-lookup"><span data-stu-id="e5189-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="e5189-142">Při spuštění příkladu bez poskytnutí konfiguračního souboru se zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="e5189-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="e5189-143">Všimněte si, že kódy hash pro řetězec jsou v obou aplikačních doménách identické.</span><span class="sxs-lookup"><span data-stu-id="e5189-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="e5189-144">Ale pokud přidáte následující konfigurační soubor do vzorového adresáře a spusťte příklad, hash kódy pro stejný řetězec budou lišit podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5189-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="e5189-145">Pokud konfigurační soubor je k dispozici, příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="e5189-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5189-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5189-146">See Also</span></span>  
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
