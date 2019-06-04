---
title: Element <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4187d266d82783ebb72073c1da92faff95352884
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489378"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="d007b-102">\<shadowCopyVerifyByTimestamp> Element</span><span class="sxs-lookup"><span data-stu-id="d007b-102">\<shadowCopyVerifyByTimestamp> Element</span></span>
<span data-ttu-id="d007b-103">Určuje, zda stínové kopírování sestavení použije výchozí chování při spuštění zavedené v rozhraní .NET Framework 4 nebo se vrátí do chování při spuštění z dřívějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d007b-103">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="d007b-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="d007b-104">\<configuration> Element</span></span>  
<span data-ttu-id="d007b-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="d007b-105">\<runtime> Element</span></span>  
<span data-ttu-id="d007b-106">\<shadowCopyVerifyByTimestamp> Element</span><span class="sxs-lookup"><span data-stu-id="d007b-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d007b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d007b-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d007b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d007b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d007b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d007b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d007b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d007b-110">Attributes</span></span>  
  
|<span data-ttu-id="d007b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d007b-111">Attribute</span></span>|<span data-ttu-id="d007b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d007b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d007b-113">enabled</span><span class="sxs-lookup"><span data-stu-id="d007b-113">enabled</span></span>|<span data-ttu-id="d007b-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d007b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d007b-115">Určuje, zda porovnání aplikační domény, které používají stínové kopírování sestavení časová razítka při spuštění, chcete-li zjistit, zda sestavení byl aktualizován před stínové kopírování sestavení.</span><span class="sxs-lookup"><span data-stu-id="d007b-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d007b-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d007b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="d007b-117">Value</span><span class="sxs-lookup"><span data-stu-id="d007b-117">Value</span></span>|<span data-ttu-id="d007b-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d007b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d007b-119">true</span><span class="sxs-lookup"><span data-stu-id="d007b-119">true</span></span>|<span data-ttu-id="d007b-120">Při spuštění zkopíruje pouze sestavení, které byly aktualizovány od posledního byly zkopírovány do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="d007b-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d007b-121">Toto je výchozí nastavení pro rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d007b-121">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="d007b-122">false</span><span class="sxs-lookup"><span data-stu-id="d007b-122">false</span></span>|<span data-ttu-id="d007b-123">Vrátí chování při spuštění z předchozích verzí rozhraní .NET Framework, která byla zkopírujte všechny soubory při spuštění.</span><span class="sxs-lookup"><span data-stu-id="d007b-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d007b-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d007b-124">Child Elements</span></span>  
 <span data-ttu-id="d007b-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="d007b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d007b-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d007b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d007b-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="d007b-127">Element</span></span>|<span data-ttu-id="d007b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d007b-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d007b-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d007b-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d007b-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d007b-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d007b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d007b-131">Remarks</span></span>  
 <span data-ttu-id="d007b-132">Od verze rozhraní .NET Framework 4, sestavení jsou stínové kopie pouze v případě, že jejich časová razítka znamenat, že se změnily od posledního byly zkopírovány do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="d007b-132">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="d007b-133">Tím se zlepšuje dobu spuštění pro mnoho aplikací, které používají stínové kopírování sestavení, jak je popsáno v [stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d007b-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="d007b-134">Aplikace, které mají vysoké procento a četnosti aktualizací sestavení nemusí využívat tuto změnu v chování.</span><span class="sxs-lookup"><span data-stu-id="d007b-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="d007b-135">V takovém případě můžete tento element obnovit chování z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d007b-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d007b-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="d007b-136">Example</span></span>  
 <span data-ttu-id="d007b-137">Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínové kopírování v rozhraní .NET Framework 4 a vrátit se na chování při spuštění z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d007b-137">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d007b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d007b-138">See also</span></span>

- [<span data-ttu-id="d007b-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d007b-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d007b-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d007b-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="d007b-141">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="d007b-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
