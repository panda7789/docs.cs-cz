---
title: "&lt;Userandomizedstringhashalgorithm –&gt; – Element"
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
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b6231f362a30f4766ccf5a43d33fa0dc7257ad57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a><span data-ttu-id="43568-102">&lt;Userandomizedstringhashalgorithm –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="43568-102">&lt;UseRandomizedStringHashAlgorithm&gt; Element</span></span>
<span data-ttu-id="43568-103">Určuje, zda modul common language runtime vypočítá na kódů hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="43568-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="43568-104">\<configuration></span></span>  
<span data-ttu-id="43568-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="43568-105">\<runtime></span></span>  
<span data-ttu-id="43568-106">\<Userandomizedstringhashalgorithm – ></span><span class="sxs-lookup"><span data-stu-id="43568-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43568-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43568-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43568-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="43568-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43568-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="43568-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43568-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="43568-110">Attributes</span></span>  
  
|<span data-ttu-id="43568-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="43568-111">Attribute</span></span>|<span data-ttu-id="43568-112">Popis</span><span class="sxs-lookup"><span data-stu-id="43568-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="43568-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="43568-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="43568-114">Určuje, zda jsou na vypočteny kódů hash pro řetězce na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="43568-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="43568-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="43568-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="43568-116">Value</span></span>|<span data-ttu-id="43568-117">Popis</span><span class="sxs-lookup"><span data-stu-id="43568-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="43568-118">Modul common language runtime nepočítá na kódů hash pro řetězce na základě domény aplikace; jeden algoritmus se používá k výpočtu kódů hash řetězec.</span><span class="sxs-lookup"><span data-stu-id="43568-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="43568-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="43568-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="43568-120">Modul common language runtime vypočítá kódů hash pro řetězce na na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="43568-121">Identické řetězce v různých doménách aplikace a v různých procesů bude mít jiné hash – kódy.</span><span class="sxs-lookup"><span data-stu-id="43568-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43568-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="43568-122">Child Elements</span></span>  
 <span data-ttu-id="43568-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="43568-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43568-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="43568-124">Parent Elements</span></span>  
  
|<span data-ttu-id="43568-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="43568-125">Element</span></span>|<span data-ttu-id="43568-126">Popis</span><span class="sxs-lookup"><span data-stu-id="43568-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="43568-127">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43568-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="43568-128">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="43568-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43568-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43568-129">Remarks</span></span>  
 <span data-ttu-id="43568-130">Ve výchozím nastavení <xref:System.StringComparer> třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda používat jeden algoritmus hash, která vytvoří hodnotu hash konzistentní napříč doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="43568-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="43568-131">Jde o ekvivalent nastavení `enabled` atribut `<UseRandomizedStringHashAlgorithm>` element `0`.</span><span class="sxs-lookup"><span data-stu-id="43568-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="43568-132">Toto je algoritmus hash, které jsou používány [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43568-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="43568-133"><xref:System.StringComparer> Třídy a <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> metoda můžete také použít jiný algoritmus hash, která vypočítá kódů hash na na základě domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="43568-134">Hash – kódy pro ekvivalentní řetězce v důsledku toho budou lišit napříč doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="43568-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="43568-135">Toto je funkce přihlášení; Chcete-li jej využít, musíte nastavit `enabled` atribut `<UseRandomizedStringHashAlgorithm>` element `1`.</span><span class="sxs-lookup"><span data-stu-id="43568-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="43568-136">Operace o(1), která je obvykle vyhledávací řetězec v zatřiďovací tabulku.</span><span class="sxs-lookup"><span data-stu-id="43568-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="43568-137">Pokud dojde k velký počet kolizí, však může vyhledávání stát O (n<sup>2</sup>) operaci.</span><span class="sxs-lookup"><span data-stu-id="43568-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="43568-138">Můžete použít `<UseRandomizedStringHashAlgorithm>` konfigurace element nevygeneruje náhodných algoritmu hash pro doménu aplikace, která zase omezuje počet potenciální kolize, zejména v případě, že jsou klíče, z nichž jsou vypočítávány kódů hash založené na vstupní data uživatelé.</span><span class="sxs-lookup"><span data-stu-id="43568-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43568-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="43568-139">Example</span></span>  
 <span data-ttu-id="43568-140">V následujícím příkladu definuje `DisplayString` třídu, která zahrnuje privátní řetězcová konstanta, `s`, jehož hodnota je "Toto je řetězec".</span><span class="sxs-lookup"><span data-stu-id="43568-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="43568-141">Zahrnuje také `ShowStringHashCode` metoda, která zobrazuje hodnotu řetězce a jeho hodnota hash společně s název domény aplikace, ve kterém metoda provádí.</span><span class="sxs-lookup"><span data-stu-id="43568-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="43568-142">Když spustíte příklad bez zadávání konfiguračního souboru, zobrazí se výstup podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="43568-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="43568-143">Upozorňujeme, že kódů hash pro řetězec jsou identické v doménách dvě aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="43568-144">Ale pokud přidáte následující konfigurační soubor do adresáře v příkladu a spusťte v příkladu, kódů hash pro stejný řetězec budou lišit podle domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="43568-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="43568-145">Pokud konfigurační soubor, v příkladu se zobrazí následující výstup:</span><span class="sxs-lookup"><span data-stu-id="43568-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="43568-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="43568-146">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
