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
ms.openlocfilehash: c13dd2f00e08539d2ba502058c74aa4a1525e3ff
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816120"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="098cb-102">\<enforcefipspolicy – > – Element</span><span class="sxs-lookup"><span data-stu-id="098cb-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="098cb-103">Určuje, jestli chcete vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu se informace o zpracování normy FIPS (Federal).</span><span class="sxs-lookup"><span data-stu-id="098cb-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="098cb-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="098cb-104">\<configuration> Element</span></span>  
<span data-ttu-id="098cb-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="098cb-105">\<runtime> Element</span></span>  
<span data-ttu-id="098cb-106">\<enforcefipspolicy – > – Element</span><span class="sxs-lookup"><span data-stu-id="098cb-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098cb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="098cb-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="098cb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="098cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="098cb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="098cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="098cb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="098cb-110">Attributes</span></span>  
  
|<span data-ttu-id="098cb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="098cb-111">Attribute</span></span>|<span data-ttu-id="098cb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="098cb-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="098cb-113">enabled</span><span class="sxs-lookup"><span data-stu-id="098cb-113">enabled</span></span>|<span data-ttu-id="098cb-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="098cb-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="098cb-115">Určuje, jestli se má povolit vynucení požadavek konfigurace počítače, musí být kryptografické algoritmy kompatibilní se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="098cb-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="098cb-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="098cb-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="098cb-117">Value</span><span class="sxs-lookup"><span data-stu-id="098cb-117">Value</span></span>|<span data-ttu-id="098cb-118">Popis</span><span class="sxs-lookup"><span data-stu-id="098cb-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="098cb-119">V případě, že váš počítač je nakonfigurován tak, aby vyžadovala kryptografické algoritmy pro rozpoznávání kompatibilní se standardem FIPS, tento požadavek se nevynutí.</span><span class="sxs-lookup"><span data-stu-id="098cb-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="098cb-120">Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody pro danou třídu vyvolat výjimky při jejich spuštění na tomto počítači.</span><span class="sxs-lookup"><span data-stu-id="098cb-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="098cb-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="098cb-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="098cb-122">Kryptografické algoritmy, které používají aplikace nejsou musí být v souladu se standardem FIPS, bez ohledu na konfigurace počítače.</span><span class="sxs-lookup"><span data-stu-id="098cb-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="098cb-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="098cb-123">Child Elements</span></span>  
 <span data-ttu-id="098cb-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="098cb-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="098cb-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="098cb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="098cb-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="098cb-126">Element</span></span>|<span data-ttu-id="098cb-127">Popis</span><span class="sxs-lookup"><span data-stu-id="098cb-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="098cb-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="098cb-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="098cb-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="098cb-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="098cb-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="098cb-130">Remarks</span></span>  
 <span data-ttu-id="098cb-131">Od verze rozhraní .NET Framework 2.0, vytváření třídy, které implementují kryptografické algoritmy řídí konfiguraci počítače.</span><span class="sxs-lookup"><span data-stu-id="098cb-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="098cb-132">Pokud je počítač nakonfigurovaný tak, aby vyžadovala algoritmy být v souladu se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoliv pokus o vytvoření instance této třídy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="098cb-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="098cb-133">Vyvolat konstruktory <xref:System.InvalidOperationException> výjimky, a `Create` vyvolání metody <xref:System.Reflection.TargetInvocationException> výjimka s vnitřní <xref:System.InvalidOperationException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="098cb-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="098cb-134">Pokud vaše aplikace funguje na počítačích, jejichž konfigurací vyžadovat dodržování standardu FIPS a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, aby se zabránilo common language runtime (CLR) z můžete tento prvek v konfiguračním souboru vynucování kompatibilita se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="098cb-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="098cb-135">Tento prvek byla zavedena v rozhraní .NET Framework 2.0 Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="098cb-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="098cb-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="098cb-136">Example</span></span>  
 <span data-ttu-id="098cb-137">Následující příklad ukazuje, jak zabránit CLR vynucování kompatibilita se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="098cb-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="098cb-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="098cb-138">See also</span></span>

- [<span data-ttu-id="098cb-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="098cb-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="098cb-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="098cb-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="098cb-141">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="098cb-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
