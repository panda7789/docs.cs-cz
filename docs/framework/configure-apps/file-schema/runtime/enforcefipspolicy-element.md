---
title: "&lt;enforcefipspolicy –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fb8cb1ea4d011eb25aee14ddd53d3dc882f75d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltenforcefipspolicygt-element"></a><span data-ttu-id="b1db6-102">&lt;enforcefipspolicy –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="b1db6-102">&lt;enforceFIPSPolicy&gt; Element</span></span>
<span data-ttu-id="b1db6-103">Určuje, jestli vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu s na zpracování standardů FIPS (Federal Information).</span><span class="sxs-lookup"><span data-stu-id="b1db6-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="b1db6-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="b1db6-104">\<configuration> Element</span></span>  
<span data-ttu-id="b1db6-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="b1db6-105">\<runtime> Element</span></span>  
<span data-ttu-id="b1db6-106">\<enforcefipspolicy – > elementu</span><span class="sxs-lookup"><span data-stu-id="b1db6-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1db6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1db6-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1db6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1db6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1db6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1db6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1db6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1db6-110">Attributes</span></span>  
  
|<span data-ttu-id="b1db6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1db6-111">Attribute</span></span>|<span data-ttu-id="b1db6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b1db6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1db6-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="b1db6-113">enabled</span></span>|<span data-ttu-id="b1db6-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b1db6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b1db6-115">Určuje, jestli se má povolit vynucení požadavek konfigurace počítače, musí být kryptografické algoritmy kompatibilní s FIPS.</span><span class="sxs-lookup"><span data-stu-id="b1db6-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b1db6-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="b1db6-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="b1db6-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b1db6-117">Value</span></span>|<span data-ttu-id="b1db6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="b1db6-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="b1db6-119">Pokud váš počítač je nakonfigurován tak, aby vyžadovala kryptografické algoritmy být kompatibilní se standardem FIPS, že požadavek je vyžadována.</span><span class="sxs-lookup"><span data-stu-id="b1db6-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="b1db6-120">Pokud třída implementuje algoritmu, který není kompatibilní s FIPS, konstruktorů nebo `Create` metody pro tuto třídu generování výjimek, pokud jsou v tomto počítači spustit.</span><span class="sxs-lookup"><span data-stu-id="b1db6-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="b1db6-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b1db6-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="b1db6-122">Kryptografické algoritmy, které používají aplikace nejsou nemusí být kompatibilní s FIPS, bez ohledu na konfigurace počítače.</span><span class="sxs-lookup"><span data-stu-id="b1db6-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1db6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1db6-123">Child Elements</span></span>  
 <span data-ttu-id="b1db6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1db6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1db6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1db6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="b1db6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1db6-126">Element</span></span>|<span data-ttu-id="b1db6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="b1db6-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b1db6-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1db6-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b1db6-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b1db6-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1db6-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1db6-130">Remarks</span></span>  
 <span data-ttu-id="b1db6-131">Od verze rozhraní .NET Framework 2.0, řídí vytváření třídy, které implementují kryptografické algoritmy konfiguraci počítače.</span><span class="sxs-lookup"><span data-stu-id="b1db6-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="b1db6-132">Pokud je počítač nakonfigurovaný tak, aby vyžadovala algoritmy s cílem být v souladu se standardem FIPS, a třída implementuje algoritmu, který není kompatibilní s FIPS, pokusy o vytvoření instance této třídy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="b1db6-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="b1db6-133">Konstruktory throw <xref:System.InvalidOperationException> výjimka, a `Create` metody throw <xref:System.Reflection.TargetInvocationException> výjimka vnitřní <xref:System.InvalidOperationException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="b1db6-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="b1db6-134">Pokud vaše aplikace běží na počítačích, jejichž konfigurace vyžadují kompatibilitu se standardem FIPS, a vaše aplikace používá algoritmus, který není kompatibilní s FIPS, aby se zabránilo common language runtime (CLR) z můžete tento element v konfiguračním souboru vynucování soulad se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="b1db6-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="b1db6-135">Tento element byla zavedena v [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1db6-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1db6-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1db6-136">Example</span></span>  
 <span data-ttu-id="b1db6-137">Následující příklad ukazuje, jak zabránit vynucovat soulad se standardem FIPS modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="b1db6-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1db6-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1db6-138">See Also</span></span>  
 [<span data-ttu-id="b1db6-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b1db6-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="b1db6-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b1db6-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="b1db6-141">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="b1db6-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
