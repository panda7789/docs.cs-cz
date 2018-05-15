---
title: '&lt;legacycorruptedstateexceptionspolicy –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6228aaf4c7da70337d9d1a99adcb78f71a0039b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltlegacycorruptedstateexceptionspolicygt-element"></a><span data-ttu-id="dd9ac-102">&lt;legacycorruptedstateexceptionspolicy –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="dd9ac-102">&lt;legacyCorruptedStateExceptionsPolicy&gt; Element</span></span>
<span data-ttu-id="dd9ac-103">Určuje, zda modul common language runtime umožňuje spravovaného kódu k zachycení narušení přístupu a ostatní výjimky v poškozeném stavu.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="dd9ac-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="dd9ac-104">\<configuration></span></span>  
<span data-ttu-id="dd9ac-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="dd9ac-105">\<runtime></span></span>  
<span data-ttu-id="dd9ac-106">\<legacycorruptedstateexceptionspolicy – ></span><span class="sxs-lookup"><span data-stu-id="dd9ac-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd9ac-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd9ac-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd9ac-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd9ac-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dd9ac-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd9ac-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd9ac-110">Attributes</span></span>  
  
|<span data-ttu-id="dd9ac-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="dd9ac-111">Attribute</span></span>|<span data-ttu-id="dd9ac-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dd9ac-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="dd9ac-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="dd9ac-114">Určuje, že aplikace zachytí poškozování stavu výjimky selhání například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="dd9ac-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="dd9ac-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="dd9ac-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="dd9ac-116">Value</span></span>|<span data-ttu-id="dd9ac-117">Popis</span><span class="sxs-lookup"><span data-stu-id="dd9ac-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="dd9ac-118">Aplikace nebude catch poškozování stavu výjimky selhání například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="dd9ac-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="dd9ac-120">Aplikace zachytí poškozování stavu výjimky selhání například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd9ac-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd9ac-121">Child Elements</span></span>  
 <span data-ttu-id="dd9ac-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="dd9ac-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd9ac-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd9ac-123">Parent Elements</span></span>  
  
|<span data-ttu-id="dd9ac-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd9ac-124">Element</span></span>|<span data-ttu-id="dd9ac-125">Popis</span><span class="sxs-lookup"><span data-stu-id="dd9ac-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="dd9ac-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="dd9ac-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd9ac-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd9ac-128">Remarks</span></span>  
 <span data-ttu-id="dd9ac-129">V rozhraní .NET Framework verze 3.5 a starší modul common language runtime povoleno spravovaného kódu k zachycení výjimky, které byly vyvolány státy poškozená procesu.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="dd9ac-130">Narušení přístupu je příklad tohoto typu výjimky.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="dd9ac-131">Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]spravovaný kód už zachytí tyto typy výjimek v `catch` bloky.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-131">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="dd9ac-132">Můžete však přepsat tuto změnu a udržovat ošetření výjimky v poškozeném stavu dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="dd9ac-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
-   <span data-ttu-id="dd9ac-133">Nastavte `<legacyCorruptedStateExceptionsPolicy>` elementu `enabled` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="dd9ac-134">Toto nastavení je použité processwide a ovlivňuje všechny metody.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="dd9ac-135">-nebo-</span><span class="sxs-lookup"><span data-stu-id="dd9ac-135">-or-</span></span>  
  
-   <span data-ttu-id="dd9ac-136">Použít <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atribut metodu, která obsahuje výjimky `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="dd9ac-137">Tento element konfigurace je k dispozici pouze v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-137">This configuration element is available only in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd9ac-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd9ac-138">Example</span></span>  
 <span data-ttu-id="dd9ac-139">Následující příklad ukazuje, jak určit, že aplikace by měla vrátit k chování před [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]a catch všechny poskozeny stavu výjimky selhání.</span><span class="sxs-lookup"><span data-stu-id="dd9ac-139">The following example shows how to specify that the application should revert to the behavior before the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd9ac-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd9ac-140">See Also</span></span>  
 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>  
 [<span data-ttu-id="dd9ac-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="dd9ac-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="dd9ac-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="dd9ac-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
