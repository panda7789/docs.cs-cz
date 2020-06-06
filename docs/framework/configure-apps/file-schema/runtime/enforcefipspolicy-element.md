---
title: Element <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117376"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="32cbc-102">Element \<enforceFIPSPolicy></span><span class="sxs-lookup"><span data-stu-id="32cbc-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="32cbc-103">Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).</span><span class="sxs-lookup"><span data-stu-id="32cbc-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="32cbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32cbc-104">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32cbc-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="32cbc-105">Attributes and Elements</span></span>  
 <span data-ttu-id="32cbc-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="32cbc-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32cbc-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="32cbc-107">Attributes</span></span>  
  
|<span data-ttu-id="32cbc-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="32cbc-108">Attribute</span></span>|<span data-ttu-id="32cbc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="32cbc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32cbc-110">enabled</span><span class="sxs-lookup"><span data-stu-id="32cbc-110">enabled</span></span>|<span data-ttu-id="32cbc-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="32cbc-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="32cbc-112">Určuje, jestli se má povolit vynucení požadavku na konfiguraci počítače, že kryptografické algoritmy musí být kompatibilní se standardem FIPS.</span><span class="sxs-lookup"><span data-stu-id="32cbc-112">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="32cbc-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="32cbc-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="32cbc-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="32cbc-114">Value</span></span>|<span data-ttu-id="32cbc-115">Description</span><span class="sxs-lookup"><span data-stu-id="32cbc-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="32cbc-116">Pokud je počítač nakonfigurován tak, aby vyžadoval kryptografické algoritmy kompatibilní se standardem FIPS, bude tento požadavek vynucen.</span><span class="sxs-lookup"><span data-stu-id="32cbc-116">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="32cbc-117">Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody této třídy vyvolávají výjimky při jejich spuštění na daném počítači.</span><span class="sxs-lookup"><span data-stu-id="32cbc-117">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="32cbc-118">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="32cbc-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="32cbc-119">Kryptografické algoritmy, které aplikace používá, nemusí být kompatibilní se standardem FIPS bez ohledu na konfiguraci počítače.</span><span class="sxs-lookup"><span data-stu-id="32cbc-119">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32cbc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="32cbc-120">Child Elements</span></span>  
 <span data-ttu-id="32cbc-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="32cbc-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32cbc-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="32cbc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="32cbc-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="32cbc-123">Element</span></span>|<span data-ttu-id="32cbc-124">Description</span><span class="sxs-lookup"><span data-stu-id="32cbc-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="32cbc-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32cbc-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="32cbc-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="32cbc-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32cbc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="32cbc-127">Remarks</span></span>  
 <span data-ttu-id="32cbc-128">Počínaje .NET Framework 2,0 se vytváření tříd, které implementují kryptografické algoritmy, řídí konfigurací počítače.</span><span class="sxs-lookup"><span data-stu-id="32cbc-128">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="32cbc-129">Pokud je počítač nakonfigurován tak, aby vyžadoval, aby algoritmy byly kompatibilní se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoli pokus o vytvoření instance této třídy vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="32cbc-129">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="32cbc-130">Konstruktory vyvolávají <xref:System.InvalidOperationException> výjimku a `Create` metody vyvolávají <xref:System.Reflection.TargetInvocationException> výjimku s vnitřní <xref:System.InvalidOperationException> výjimkou.</span><span class="sxs-lookup"><span data-stu-id="32cbc-130">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="32cbc-131">Pokud vaše aplikace běží na počítačích, jejichž konfigurace vyžaduje dodržování předpisů pomocí standardu FIPS, a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, můžete použít tento prvek v konfiguračním souboru, abyste zabránili vynucování dodržování standardů FIPS v modulu Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="32cbc-131">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="32cbc-132">Tento prvek byl představen v aktualizaci Service Pack 1 pro .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="32cbc-132">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32cbc-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="32cbc-133">Example</span></span>  
 <span data-ttu-id="32cbc-134">Následující příklad ukazuje, jak zabránit CLR v vynucování dodržování standardů FIPS.</span><span class="sxs-lookup"><span data-stu-id="32cbc-134">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="32cbc-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="32cbc-135">See also</span></span>

- [<span data-ttu-id="32cbc-136">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="32cbc-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="32cbc-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="32cbc-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="32cbc-138">Kryptografický model</span><span class="sxs-lookup"><span data-stu-id="32cbc-138">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
