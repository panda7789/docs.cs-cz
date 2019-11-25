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
ms.openlocfilehash: 3863bc1376d89ef804022fb9c87fac3a25fc910f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968834"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="3e1eb-102">\<element > UseRandomizedStringHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="3e1eb-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="3e1eb-103">Určuje, zda modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="3e1eb-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3e1eb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3e1eb-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3e1eb-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3e1eb-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm >**</span><span class="sxs-lookup"><span data-stu-id="3e1eb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1eb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e1eb-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e1eb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3e1eb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3e1eb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e1eb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3e1eb-110">Attributes</span></span>  
  
|<span data-ttu-id="3e1eb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3e1eb-111">Attribute</span></span>|<span data-ttu-id="3e1eb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3e1eb-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3e1eb-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3e1eb-114">Určuje, zda jsou kódy hash pro řetězce počítány na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3e1eb-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="3e1eb-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3e1eb-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3e1eb-116">Value</span></span>|<span data-ttu-id="3e1eb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3e1eb-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="3e1eb-118">Modul CLR (Common Language Runtime) nepočítá kódy hash pro řetězce na základě domény aplikace. k výpočtu řetězcových kódů hash se používá jeden algoritmus.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="3e1eb-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="3e1eb-120">Modul CLR (Common Language Runtime) vypočítá kódy hash pro řetězce v jednotlivých doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="3e1eb-121">Identické řetězce v různých aplikačních doménách a v různých procesech budou mít různé kódy hash.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e1eb-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3e1eb-122">Child Elements</span></span>  
 <span data-ttu-id="3e1eb-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="3e1eb-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e1eb-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3e1eb-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3e1eb-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="3e1eb-125">Element</span></span>|<span data-ttu-id="3e1eb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="3e1eb-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3e1eb-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3e1eb-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e1eb-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e1eb-129">Remarks</span></span>  
 <span data-ttu-id="3e1eb-130">Ve výchozím nastavení používá třída <xref:System.StringComparer> a metoda <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> jeden algoritmus hash, který vytváří konzistentní kód hash napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="3e1eb-131">To je ekvivalentní nastavení atributu `enabled` `<UseRandomizedStringHashAlgorithm>` elementu na `0`.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="3e1eb-132">Toto je algoritmus hash používaný v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="3e1eb-133">Třída <xref:System.StringComparer> a metoda <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> mohou také použít jiný algoritmus hash, který vypočítává kódy hash pro každou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="3e1eb-134">V důsledku toho se kódy hash pro ekvivalentní řetězce budou lišit napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="3e1eb-135">Toto je funkce výslovného souhlasu; abyste ho mohli využít, musíte nastavit atribut `enabled` `<UseRandomizedStringHashAlgorithm>` elementu na `1`.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="3e1eb-136">Vyhledávání řetězců v zatřiďovací tabulce je obvykle operace O (1).</span><span class="sxs-lookup"><span data-stu-id="3e1eb-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="3e1eb-137">Pokud ale dojde k velkému počtu kolizí, vyhledávání se může stát operací O (n<sup>2</sup>).</span><span class="sxs-lookup"><span data-stu-id="3e1eb-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="3e1eb-138">Můžete použít prvek konfigurace `<UseRandomizedStringHashAlgorithm>` k vygenerování náhodného algoritmu hash pro každou doménu aplikace, která zase omezuje počet potenciálních kolizí, zejména v případě, že klíče, ze kterých jsou vypočítány hodnoty hash, jsou založeny na vstupu dat mohou.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1eb-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e1eb-139">Example</span></span>  
 <span data-ttu-id="3e1eb-140">Následující příklad definuje třídu `DisplayString`, která obsahuje soukromou řetězcovou konstantu, `s`, jejíž hodnota je "Toto je řetězec."</span><span class="sxs-lookup"><span data-stu-id="3e1eb-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="3e1eb-141">Obsahuje také metodu `ShowStringHashCode`, která zobrazuje hodnotu řetězce a jeho hashový kód spolu s názvem domény aplikace, ve které je metoda prováděna.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="3e1eb-142">Pokud spustíte příklad bez zadání konfiguračního souboru, zobrazí se výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="3e1eb-143">Všimněte si, že kódy hash pro řetězec jsou identické ve dvou doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="3e1eb-144">Pokud však do adresáře příkladu přidáte následující konfigurační soubor a poté spustíte příklad, kódy hash stejného řetězce se budou lišit podle aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="3e1eb-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="3e1eb-145">Když je konfigurační soubor přítomen, v příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="3e1eb-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e1eb-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e1eb-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
