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
ms.openlocfilehash: eb28eddf7e9f13bceaf47de28633073f59f3920d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663743"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="36f59-102">\<enforceFIPSPolicy – element ></span><span class="sxs-lookup"><span data-stu-id="36f59-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="36f59-103">Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).</span><span class="sxs-lookup"><span data-stu-id="36f59-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="36f59-104">\<Element > Konfigurace</span><span class="sxs-lookup"><span data-stu-id="36f59-104">\<configuration> Element</span></span>  
<span data-ttu-id="36f59-105">\<Běhový > element</span><span class="sxs-lookup"><span data-stu-id="36f59-105">\<runtime> Element</span></span>  
<span data-ttu-id="36f59-106">\<enforceFIPSPolicy – element ></span><span class="sxs-lookup"><span data-stu-id="36f59-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f59-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36f59-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36f59-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="36f59-108">Attributes and Elements</span></span>  
 <span data-ttu-id="36f59-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="36f59-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36f59-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="36f59-110">Attributes</span></span>  
  
|<span data-ttu-id="36f59-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="36f59-111">Attribute</span></span>|<span data-ttu-id="36f59-112">Popis</span><span class="sxs-lookup"><span data-stu-id="36f59-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36f59-113">enabled</span><span class="sxs-lookup"><span data-stu-id="36f59-113">enabled</span></span>|<span data-ttu-id="36f59-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="36f59-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="36f59-115">Určuje, jestli se má povolit vynucení požadavku na konfiguraci počítače, že kryptografické algoritmy musí být kompatibilní se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="36f59-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="36f59-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="36f59-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="36f59-117">Value</span><span class="sxs-lookup"><span data-stu-id="36f59-117">Value</span></span>|<span data-ttu-id="36f59-118">Popis</span><span class="sxs-lookup"><span data-stu-id="36f59-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="36f59-119">Pokud je počítač nakonfigurován tak, aby vyžadoval kryptografické algoritmy kompatibilní se standardem FIPS, bude tento požadavek vynucen.</span><span class="sxs-lookup"><span data-stu-id="36f59-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="36f59-120">Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody této třídy vyvolávají výjimky při jejich spuštění na daném počítači.</span><span class="sxs-lookup"><span data-stu-id="36f59-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="36f59-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="36f59-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="36f59-122">Kryptografické algoritmy, které aplikace používá, nemusí být kompatibilní se standardem FIPS bez ohledu na konfiguraci počítače.</span><span class="sxs-lookup"><span data-stu-id="36f59-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36f59-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36f59-123">Child Elements</span></span>  
 <span data-ttu-id="36f59-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="36f59-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36f59-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="36f59-125">Parent Elements</span></span>  
  
|<span data-ttu-id="36f59-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="36f59-126">Element</span></span>|<span data-ttu-id="36f59-127">Popis</span><span class="sxs-lookup"><span data-stu-id="36f59-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="36f59-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="36f59-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="36f59-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="36f59-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36f59-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36f59-130">Remarks</span></span>  
 <span data-ttu-id="36f59-131">Počínaje .NET Framework 2,0 se vytváření tříd, které implementují kryptografické algoritmy, řídí konfigurací počítače.</span><span class="sxs-lookup"><span data-stu-id="36f59-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="36f59-132">Pokud je počítač nakonfigurován tak, aby vyžadoval, aby algoritmy byly kompatibilní se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoli pokus o vytvoření instance této třídy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="36f59-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="36f59-133">Konstruktory vyvolávají <xref:System.InvalidOperationException> výjimku a `Create` metody vyvolávají <xref:System.Reflection.TargetInvocationException> výjimku s vnitřní <xref:System.InvalidOperationException> výjimkou.</span><span class="sxs-lookup"><span data-stu-id="36f59-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="36f59-134">Pokud vaše aplikace běží na počítačích, jejichž konfigurace vyžaduje kompatibilitu se standardem FIPS, a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, můžete použít tento prvek v konfiguračním souboru, aby nedocházelo k tomu, že modul CLR (Common Language Runtime) z vynucování dodržování standardů FIPS.</span><span class="sxs-lookup"><span data-stu-id="36f59-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="36f59-135">Tento prvek byl představen v aktualizaci Service Pack 1 pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="36f59-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36f59-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="36f59-136">Example</span></span>  
 <span data-ttu-id="36f59-137">Následující příklad ukazuje, jak zabránit CLR v vynucování dodržování standardů FIPS.</span><span class="sxs-lookup"><span data-stu-id="36f59-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36f59-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36f59-138">See also</span></span>

- [<span data-ttu-id="36f59-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="36f59-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="36f59-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="36f59-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="36f59-141">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="36f59-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
