---
title: '&lt;shadowCopyVerifyByTimestamp&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a97c8708c7d57d1a8f5335ef19e8e74cb6487276
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610902"
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a><span data-ttu-id="aa970-102">&lt;shadowCopyVerifyByTimestamp&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="aa970-102">&lt;shadowCopyVerifyByTimestamp&gt; Element</span></span>
<span data-ttu-id="aa970-103">Určuje, zda stínové kopírování sestavení použije výchozí chování při spouštění zavedený [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spuštění z dřívějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa970-103">Specifies whether shadow copying uses the default startup behavior introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="aa970-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="aa970-104">\<configuration> Element</span></span>  
<span data-ttu-id="aa970-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="aa970-105">\<runtime> Element</span></span>  
<span data-ttu-id="aa970-106">\<shadowCopyVerifyByTimestamp > – Element</span><span class="sxs-lookup"><span data-stu-id="aa970-106">\<shadowCopyVerifyByTimestamp> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa970-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa970-107">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa970-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aa970-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aa970-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aa970-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa970-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="aa970-110">Attributes</span></span>  
  
|<span data-ttu-id="aa970-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="aa970-111">Attribute</span></span>|<span data-ttu-id="aa970-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aa970-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa970-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="aa970-113">enabled</span></span>|<span data-ttu-id="aa970-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="aa970-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="aa970-115">Určuje, zda porovnání aplikační domény, které používají stínové kopírování sestavení časová razítka při spuštění, chcete-li zjistit, zda sestavení byl aktualizován před stínové kopírování sestavení.</span><span class="sxs-lookup"><span data-stu-id="aa970-115">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="aa970-116">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="aa970-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="aa970-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="aa970-117">Value</span></span>|<span data-ttu-id="aa970-118">Popis</span><span class="sxs-lookup"><span data-stu-id="aa970-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aa970-119">true</span><span class="sxs-lookup"><span data-stu-id="aa970-119">true</span></span>|<span data-ttu-id="aa970-120">Při spuštění zkopíruje pouze sestavení, které byly aktualizovány od posledního byly zkopírovány do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="aa970-120">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="aa970-121">Toto je výchozí nastavení pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aa970-121">This is the default for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>|  
|<span data-ttu-id="aa970-122">false</span><span class="sxs-lookup"><span data-stu-id="aa970-122">false</span></span>|<span data-ttu-id="aa970-123">Vrátí chování při spuštění z předchozích verzí rozhraní .NET Framework, která byla zkopírujte všechny soubory při spuštění.</span><span class="sxs-lookup"><span data-stu-id="aa970-123">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa970-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aa970-124">Child Elements</span></span>  
 <span data-ttu-id="aa970-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="aa970-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa970-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aa970-126">Parent Elements</span></span>  
  
|<span data-ttu-id="aa970-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="aa970-127">Element</span></span>|<span data-ttu-id="aa970-128">Popis</span><span class="sxs-lookup"><span data-stu-id="aa970-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aa970-129">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa970-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aa970-130">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="aa970-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa970-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa970-131">Remarks</span></span>  
 <span data-ttu-id="aa970-132">Počínaje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], sestavení jsou stínové kopie pouze v případě, že jejich časová razítka znamenat, že se změnily od posledního byly zkopírovány do adresáře stínové kopie.</span><span class="sxs-lookup"><span data-stu-id="aa970-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="aa970-133">Tím se zlepšuje dobu spuštění pro mnoho aplikací, které používají stínové kopírování sestavení, jak je popsáno v [stínové kopírování sestavení](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="aa970-133">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="aa970-134">Aplikace, které mají vysoké procento a četnosti aktualizací sestavení nemusí využívat tuto změnu v chování.</span><span class="sxs-lookup"><span data-stu-id="aa970-134">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="aa970-135">V takovém případě můžete tento element obnovit chování z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa970-135">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa970-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa970-136">Example</span></span>  
 <span data-ttu-id="aa970-137">Následující příklad ukazuje, jak zakázat výchozí chování při spouštění stínové kopírování sestavení v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]a vrátit se na chování při spuštění z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa970-137">The following example shows how to disable the default startup behavior of shadow copying in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa970-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa970-138">See Also</span></span>  
- [<span data-ttu-id="aa970-139">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="aa970-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="aa970-140">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="aa970-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="aa970-141">Stínové kopírování sestavení</span><span class="sxs-lookup"><span data-stu-id="aa970-141">Shadow Copying Assemblies</span></span>](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
