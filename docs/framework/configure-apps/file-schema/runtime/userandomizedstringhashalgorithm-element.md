---
title: Element <UseRandomizedStringHashAlgorithm>
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153774"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="2d6c4-102">\<UseRandomizedStringHashAlgorithm> Element</span><span class="sxs-lookup"><span data-stu-id="2d6c4-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="2d6c4-103">Určuje, zda běžný jazyk runtime vypočítá kódy hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="2d6c4-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d6c4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2d6c4-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2d6c4-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2d6c4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Použít RandomizedStringHashAlgorithm>**</span><span class="sxs-lookup"><span data-stu-id="2d6c4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d6c4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d6c4-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d6c4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d6c4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2d6c4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d6c4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d6c4-110">Attributes</span></span>  
  
|<span data-ttu-id="2d6c4-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2d6c4-111">Attribute</span></span>|<span data-ttu-id="2d6c4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2d6c4-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2d6c4-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2d6c4-114">Určuje, zda jsou kódy hash pro řetězce vypočteny na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2d6c4-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2d6c4-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2d6c4-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2d6c4-116">Value</span></span>|<span data-ttu-id="2d6c4-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2d6c4-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="2d6c4-118">Běžný jazyk runtime nevypočítává hash kódy pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu kódů hash řetězce.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="2d6c4-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="2d6c4-120">Běžný jazyk runtime vypočítá hash kódy pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="2d6c4-121">Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé hash kódy.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d6c4-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d6c4-122">Child Elements</span></span>  
 <span data-ttu-id="2d6c4-123">Žádné.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d6c4-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d6c4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2d6c4-125">Element</span><span class="sxs-lookup"><span data-stu-id="2d6c4-125">Element</span></span>|<span data-ttu-id="2d6c4-126">Popis</span><span class="sxs-lookup"><span data-stu-id="2d6c4-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2d6c4-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2d6c4-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d6c4-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d6c4-129">Remarks</span></span>  
 <span data-ttu-id="2d6c4-130">Ve výchozím <xref:System.StringComparer> nastavení třída <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> a metoda používají jeden algoritmus hash, který vytváří konzistentní kód hash napříč aplikačními doménami.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="2d6c4-131">To je ekvivalentní `enabled` nastavení atributu `<UseRandomizedStringHashAlgorithm>` `0`prvku .</span><span class="sxs-lookup"><span data-stu-id="2d6c4-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="2d6c4-132">Toto je algoritmus hash používaný v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="2d6c4-133">Třída <xref:System.StringComparer> a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda můžete také použít jiný algoritmus hash, který vypočítá hash kódy na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="2d6c4-134">V důsledku toho hash kódy pro ekvivalentní řetězce se budou lišit v rámci aplikačních domén.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="2d6c4-135">Jedná se o funkci opt-in; chcete-li jej využít, je `enabled` nutné `<UseRandomizedStringHashAlgorithm>` nastavit `1`atribut prvku na .</span><span class="sxs-lookup"><span data-stu-id="2d6c4-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="2d6c4-136">Vyhledávání řetězců v tabulce hash je obvykle operace O(1).</span><span class="sxs-lookup"><span data-stu-id="2d6c4-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="2d6c4-137">Pokud však dojde k velkému počtu kolizí, může se vyhledávání stát operací O(n<sup>2).</sup></span><span class="sxs-lookup"><span data-stu-id="2d6c4-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="2d6c4-138">`<UseRandomizedStringHashAlgorithm>` Konfigurační prvek můžete použít ke generování algoritmu náhodného hash pro každý doméně aplikace, což zase omezuje počet potenciálních kolizí, zejména pokud jsou klíče, ze kterých jsou vypočteny hash kódy, založeny na vstupu dat uživateli.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d6c4-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d6c4-139">Example</span></span>  
 <span data-ttu-id="2d6c4-140">Následující příklad definuje `DisplayString` třídu, která obsahuje `s`konstantu soukromého řetězce , jejíž hodnota je "Toto je řetězec."</span><span class="sxs-lookup"><span data-stu-id="2d6c4-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="2d6c4-141">Obsahuje také `ShowStringHashCode` metodu, která zobrazuje hodnotu řetězce a jeho kód hash spolu s názvem domény aplikace, ve které je metoda spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="2d6c4-142">Při spuštění příkladu bez zadání konfiguračního souboru se zobrazí výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="2d6c4-143">Všimněte si, že hash kódy pro řetězec jsou identické ve dvou doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="2d6c4-144">Pokud však do adresáře příkladu přidáte následující konfigurační soubor a potom spusťte příklad, kódy hash pro stejný řetězec se budou lišit podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d6c4-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2d6c4-145">Pokud je konfigurační soubor k dispozici, v příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2d6c4-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="2d6c4-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d6c4-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
