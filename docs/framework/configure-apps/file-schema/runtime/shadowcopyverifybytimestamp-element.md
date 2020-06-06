---
title: Element <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115731"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="44911-102">Element \<shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="44911-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="44911-103">Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44911-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="44911-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44911-104">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44911-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44911-105">Attributes and Elements</span></span>  
 <span data-ttu-id="44911-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44911-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44911-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="44911-107">Attributes</span></span>  
  
|<span data-ttu-id="44911-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="44911-108">Attribute</span></span>|<span data-ttu-id="44911-109">Popis</span><span class="sxs-lookup"><span data-stu-id="44911-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44911-110">enabled</span><span class="sxs-lookup"><span data-stu-id="44911-110">enabled</span></span>|<span data-ttu-id="44911-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="44911-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="44911-112">Určuje, zda aplikační domény, které používají stínové kopírování, porovnávají časová razítka sestavení při spuštění, aby bylo možné určit, zda bylo sestavení Aktualizováno před stínovým kopírováním sestavení.</span><span class="sxs-lookup"><span data-stu-id="44911-112">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="44911-113">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="44911-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="44911-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="44911-114">Value</span></span>|<span data-ttu-id="44911-115">Description</span><span class="sxs-lookup"><span data-stu-id="44911-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="44911-116">true</span><span class="sxs-lookup"><span data-stu-id="44911-116">true</span></span>|<span data-ttu-id="44911-117">Při spuštění nástroje kopíruje pouze sestavení, která byla aktualizována od posledního zkopírování do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="44911-117">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="44911-118">Toto je výchozí nastavení pro .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="44911-118">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="44911-119">false (nepravda)</span><span class="sxs-lookup"><span data-stu-id="44911-119">false</span></span>|<span data-ttu-id="44911-120">Vrátí se k chování při spuštění předchozích verzí .NET Framework, což bylo při spuštění zkopírovat všechny soubory.</span><span class="sxs-lookup"><span data-stu-id="44911-120">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44911-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44911-121">Child Elements</span></span>  
 <span data-ttu-id="44911-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="44911-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44911-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44911-123">Parent Elements</span></span>  
  
|<span data-ttu-id="44911-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="44911-124">Element</span></span>|<span data-ttu-id="44911-125">Description</span><span class="sxs-lookup"><span data-stu-id="44911-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="44911-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44911-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="44911-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="44911-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44911-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44911-128">Remarks</span></span>  
 <span data-ttu-id="44911-129">Počínaje .NET Framework 4 jsou sestavení Stínová zkopírována pouze v případě, že jejich časová razítka signalizují, že se od posledního zkopírování do adresáře stínové kopie změnily.</span><span class="sxs-lookup"><span data-stu-id="44911-129">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="44911-130">To zlepšuje dobu spouštění pro mnoho aplikací, které používají stínové kopírování, jak je popsáno v tématu [stínové kopírování sestavení](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="44911-130">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="44911-131">Aplikace, které mají vysoké procento a četnost aktualizací sestavení, nemusí mít tuto změnu v chování.</span><span class="sxs-lookup"><span data-stu-id="44911-131">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="44911-132">V takovém případě můžete použít tento prvek k obnovení chování předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44911-132">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44911-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="44911-133">Example</span></span>  
 <span data-ttu-id="44911-134">Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínového kopírování v .NET Framework 4 a vrátit se k chování při spuštění předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="44911-134">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44911-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="44911-135">See also</span></span>

- [<span data-ttu-id="44911-136">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="44911-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="44911-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="44911-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="44911-138">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="44911-138">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
