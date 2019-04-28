---
title: Element <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704960"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="a7a32-102">\<enforcefipspolicy – > – Element</span><span class="sxs-lookup"><span data-stu-id="a7a32-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="a7a32-103">Určuje, jestli chcete vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu se informace o zpracování normy FIPS (Federal).</span><span class="sxs-lookup"><span data-stu-id="a7a32-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="a7a32-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="a7a32-104">\<configuration> Element</span></span>  
<span data-ttu-id="a7a32-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="a7a32-105">\<runtime> Element</span></span>  
<span data-ttu-id="a7a32-106">\<enforcefipspolicy – > – Element</span><span class="sxs-lookup"><span data-stu-id="a7a32-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a32-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7a32-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7a32-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7a32-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a7a32-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7a32-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7a32-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7a32-110">Attributes</span></span>  
  
|<span data-ttu-id="a7a32-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7a32-111">Attribute</span></span>|<span data-ttu-id="a7a32-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a7a32-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7a32-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="a7a32-113">enabled</span></span>|<span data-ttu-id="a7a32-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a7a32-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="a7a32-115">Určuje, jestli se má povolit vynucení požadavek konfigurace počítače, musí být kryptografické algoritmy kompatibilní se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="a7a32-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a7a32-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a7a32-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="a7a32-117">Value</span><span class="sxs-lookup"><span data-stu-id="a7a32-117">Value</span></span>|<span data-ttu-id="a7a32-118">Popis</span><span class="sxs-lookup"><span data-stu-id="a7a32-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="a7a32-119">V případě, že váš počítač je nakonfigurován tak, aby vyžadovala kryptografické algoritmy pro rozpoznávání kompatibilní se standardem FIPS, tento požadavek se nevynutí.</span><span class="sxs-lookup"><span data-stu-id="a7a32-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="a7a32-120">Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody pro danou třídu vyvolat výjimky při jejich spuštění na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="a7a32-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="a7a32-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a7a32-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="a7a32-122">Kryptografické algoritmy, které používají aplikace nejsou musí být v souladu se standardem FIPS, bez ohledu na konfigurace počítače.</span><span class="sxs-lookup"><span data-stu-id="a7a32-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7a32-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7a32-123">Child Elements</span></span>  
 <span data-ttu-id="a7a32-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7a32-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7a32-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7a32-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a7a32-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7a32-126">Element</span></span>|<span data-ttu-id="a7a32-127">Popis</span><span class="sxs-lookup"><span data-stu-id="a7a32-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a7a32-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7a32-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a7a32-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a7a32-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7a32-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7a32-130">Remarks</span></span>  
 <span data-ttu-id="a7a32-131">Od verze rozhraní .NET Framework 2.0, vytváření třídy, které implementují kryptografické algoritmy řídí konfiguraci počítače.</span><span class="sxs-lookup"><span data-stu-id="a7a32-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="a7a32-132">Pokud je počítač nakonfigurovaný tak, aby vyžadovala algoritmy být v souladu se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoliv pokus o vytvoření instance této třídy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="a7a32-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="a7a32-133">Vyvolat konstruktory <xref:System.InvalidOperationException> výjimky, a `Create` vyvolání metody <xref:System.Reflection.TargetInvocationException> výjimka s vnitřní <xref:System.InvalidOperationException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="a7a32-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="a7a32-134">Pokud vaše aplikace funguje na počítačích, jejichž konfigurací vyžadovat dodržování standardu FIPS a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, aby se zabránilo common language runtime (CLR) z můžete tento prvek v konfiguračním souboru vynucování kompatibilita se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="a7a32-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="a7a32-135">Tento prvek byla zavedena v [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a7a32-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a32-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7a32-136">Example</span></span>  
 <span data-ttu-id="a7a32-137">Následující příklad ukazuje, jak zabránit CLR vynucování kompatibilita se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="a7a32-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7a32-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7a32-138">See also</span></span>

- [<span data-ttu-id="a7a32-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="a7a32-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a7a32-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a7a32-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a7a32-141">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="a7a32-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
