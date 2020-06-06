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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153774"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="303d5-102">Element \<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="303d5-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="303d5-103">Určuje, zda modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a><span data-ttu-id="303d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="303d5-104">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="303d5-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="303d5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="303d5-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="303d5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="303d5-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="303d5-107">Attributes</span></span>  
  
|<span data-ttu-id="303d5-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="303d5-108">Attribute</span></span>|<span data-ttu-id="303d5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="303d5-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="303d5-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="303d5-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="303d5-111">Určuje, zda jsou kódy hash pro řetězce počítány na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-111">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="303d5-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="303d5-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="303d5-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="303d5-113">Value</span></span>|<span data-ttu-id="303d5-114">Description</span><span class="sxs-lookup"><span data-stu-id="303d5-114">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="303d5-115">Modul CLR (Common Language Runtime) nepočítá kódy hash pro řetězce na základě domény aplikace. k výpočtu řetězcových kódů hash se používá jeden algoritmus.</span><span class="sxs-lookup"><span data-stu-id="303d5-115">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="303d5-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="303d5-116">This is the default.</span></span>|  
|`1`|<span data-ttu-id="303d5-117">Modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-117">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="303d5-118">Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé kódy hash.</span><span class="sxs-lookup"><span data-stu-id="303d5-118">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="303d5-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="303d5-119">Child Elements</span></span>  
 <span data-ttu-id="303d5-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="303d5-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="303d5-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="303d5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="303d5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="303d5-122">Element</span></span>|<span data-ttu-id="303d5-123">Description</span><span class="sxs-lookup"><span data-stu-id="303d5-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="303d5-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="303d5-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="303d5-125">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="303d5-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="303d5-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="303d5-126">Remarks</span></span>  
 <span data-ttu-id="303d5-127">Ve výchozím nastavení <xref:System.StringComparer> Třída a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda používají jeden algoritmus hash, který vytváří konzistentní kód hash napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-127">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="303d5-128">To je ekvivalentní nastavení `enabled` atributu `<UseRandomizedStringHashAlgorithm>` elementu na `0` .</span><span class="sxs-lookup"><span data-stu-id="303d5-128">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="303d5-129">Toto je algoritmus hash používaný v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="303d5-129">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="303d5-130"><xref:System.StringComparer>Třída a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> Metoda mohou také používat jiný algoritmus hash, který vypočítává kódy hash pro každou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-130">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="303d5-131">V důsledku toho se kódy hash pro ekvivalentní řetězce budou lišit napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-131">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="303d5-132">Toto je funkce výslovného souhlasu; Chcete-li jej využít, je nutné nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` elementu na `1` .</span><span class="sxs-lookup"><span data-stu-id="303d5-132">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="303d5-133">Vyhledávání řetězců v zatřiďovací tabulce je obvykle operace O (1).</span><span class="sxs-lookup"><span data-stu-id="303d5-133">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="303d5-134">Pokud ale dojde k velkému počtu kolizí, vyhledávání se může stát operací O (n<sup>2</sup>).</span><span class="sxs-lookup"><span data-stu-id="303d5-134">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="303d5-135">Prvek konfigurace lze použít `<UseRandomizedStringHashAlgorithm>` k vygenerování náhodného algoritmu hash na doménu aplikace, který naopak omezuje počet potenciálních kolizí, zejména v případě, že klíče, ze kterých jsou počítány hodnoty hash, jsou založeny na vstupních datech uživatelů.</span><span class="sxs-lookup"><span data-stu-id="303d5-135">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="303d5-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="303d5-136">Example</span></span>  
 <span data-ttu-id="303d5-137">Následující příklad definuje `DisplayString` třídu, která obsahuje soukromou řetězcovou konstantu, `s` , jejíž hodnota je "Toto je řetězec."</span><span class="sxs-lookup"><span data-stu-id="303d5-137">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="303d5-138">Obsahuje také `ShowStringHashCode` metodu, která zobrazuje hodnotu řetězce a její kód hash spolu s názvem domény aplikace, ve které je metoda spuštěna.</span><span class="sxs-lookup"><span data-stu-id="303d5-138">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="303d5-139">Pokud spustíte příklad bez zadání konfiguračního souboru, zobrazí se výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="303d5-139">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="303d5-140">Všimněte si, že kódy hash pro řetězec jsou identické ve dvou doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="303d5-140">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="303d5-141">Pokud však do adresáře příkladu přidáte následující konfigurační soubor a poté spustíte příklad, kódy hash stejného řetězce se budou lišit podle aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="303d5-141">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="303d5-142">Když je konfigurační soubor přítomen, v příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="303d5-142">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="303d5-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="303d5-143">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
