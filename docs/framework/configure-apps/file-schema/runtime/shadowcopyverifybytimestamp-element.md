---
title: Element <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79d44ff255b1fc12efc6e8488eeab231b9276b90
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252310"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="87c66-102">\<shadowCopyVerifyByTimestamp – element ></span><span class="sxs-lookup"><span data-stu-id="87c66-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="87c66-103">Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c66-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
<span data-ttu-id="87c66-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="87c66-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="87c66-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="87c66-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="87c66-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<shadowCopyVerifyByTimestamp >**</span><span class="sxs-lookup"><span data-stu-id="87c66-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87c66-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87c66-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87c66-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87c66-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87c66-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87c66-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87c66-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="87c66-110">Attributes</span></span>  
  
|<span data-ttu-id="87c66-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="87c66-111">Attribute</span></span>|<span data-ttu-id="87c66-112">Popis</span><span class="sxs-lookup"><span data-stu-id="87c66-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87c66-113">enabled</span><span class="sxs-lookup"><span data-stu-id="87c66-113">enabled</span></span>|<span data-ttu-id="87c66-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="87c66-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="87c66-115">Určuje, zda aplikační domény, které používají stínové kopírování, porovnávají časová razítka sestavení při spuštění, aby bylo možné určit, zda bylo sestavení Aktualizováno před stínovým kopírováním sestavení.</span><span class="sxs-lookup"><span data-stu-id="87c66-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="87c66-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="87c66-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="87c66-117">Value</span><span class="sxs-lookup"><span data-stu-id="87c66-117">Value</span></span>|<span data-ttu-id="87c66-118">Popis</span><span class="sxs-lookup"><span data-stu-id="87c66-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="87c66-119">true</span><span class="sxs-lookup"><span data-stu-id="87c66-119">true</span></span>|<span data-ttu-id="87c66-120">Při spuštění nástroje kopíruje pouze sestavení, která byla aktualizována od posledního zkopírování do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="87c66-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="87c66-121">Toto je výchozí nastavení pro .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="87c66-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="87c66-122">false</span><span class="sxs-lookup"><span data-stu-id="87c66-122">false</span></span>|<span data-ttu-id="87c66-123">Vrátí se k chování při spuštění předchozích verzí .NET Framework, což bylo při spuštění zkopírovat všechny soubory.</span><span class="sxs-lookup"><span data-stu-id="87c66-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87c66-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87c66-124">Child Elements</span></span>  
 <span data-ttu-id="87c66-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="87c66-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87c66-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87c66-126">Parent Elements</span></span>  
  
|<span data-ttu-id="87c66-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="87c66-127">Element</span></span>|<span data-ttu-id="87c66-128">Popis</span><span class="sxs-lookup"><span data-stu-id="87c66-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="87c66-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c66-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="87c66-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="87c66-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87c66-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87c66-131">Remarks</span></span>  
 <span data-ttu-id="87c66-132">Počínaje .NET Framework 4 jsou sestavení Stínová zkopírována pouze v případě, že jejich časová razítka signalizují, že se od posledního zkopírování do adresáře stínové kopie změnily.</span><span class="sxs-lookup"><span data-stu-id="87c66-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="87c66-133">To zlepšuje dobu spouštění pro mnoho aplikací, které používají stínové kopírování, jak je popsáno v tématu [stínové kopírování sestavení](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="87c66-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="87c66-134">Aplikace, které mají vysoké procento a četnost aktualizací sestavení, nemusí mít tuto změnu v chování.</span><span class="sxs-lookup"><span data-stu-id="87c66-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="87c66-135">V takovém případě můžete použít tento prvek k obnovení chování předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c66-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87c66-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="87c66-136">Example</span></span>  
 <span data-ttu-id="87c66-137">Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínového kopírování v .NET Framework 4 a vrátit se k chování při spuštění předchozích verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c66-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="87c66-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87c66-138">See also</span></span>

- [<span data-ttu-id="87c66-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="87c66-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="87c66-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="87c66-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="87c66-141">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="87c66-141">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
