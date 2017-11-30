---
title: "&lt;Odebrat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ff1eb93a6d81f83b60e2621296e0c9d995699898
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a><span data-ttu-id="e57fa-102">&lt;Odebrat&gt; Element pro &lt;naslouchací procesy&gt; pro &lt;trasování&gt;</span><span class="sxs-lookup"><span data-stu-id="e57fa-102">&lt;remove&gt; Element for &lt;listeners&gt; for &lt;trace&gt;</span></span>
<span data-ttu-id="e57fa-103">Odebere naslouchací proces z **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="e57fa-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="e57fa-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e57fa-104">\<configuration></span></span>  
<span data-ttu-id="e57fa-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e57fa-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e57fa-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="e57fa-106">\<trace></span></span>  
<span data-ttu-id="e57fa-107">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="e57fa-107">\<listeners></span></span>  
<span data-ttu-id="e57fa-108">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="e57fa-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57fa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e57fa-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e57fa-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e57fa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e57fa-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e57fa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e57fa-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e57fa-112">Attributes</span></span>  
  
|<span data-ttu-id="e57fa-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e57fa-113">Attribute</span></span>|<span data-ttu-id="e57fa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e57fa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e57fa-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="e57fa-115">**name**</span></span>|<span data-ttu-id="e57fa-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e57fa-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e57fa-117">Název naslouchací proces odebrání **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="e57fa-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e57fa-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e57fa-118">Child Elements</span></span>  
 <span data-ttu-id="e57fa-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="e57fa-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e57fa-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e57fa-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e57fa-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="e57fa-121">Element</span></span>|<span data-ttu-id="e57fa-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e57fa-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e57fa-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e57fa-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="e57fa-124">Určuje naslouchací proces, který shromažďuje, úložiště a směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="e57fa-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="e57fa-125">Moduly pro naslouchání přesměrujte výstup trasování do příslušné cílové.</span><span class="sxs-lookup"><span data-stu-id="e57fa-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e57fa-126">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e57fa-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e57fa-127">Nakonfiguruje službu sledování technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e57fa-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e57fa-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e57fa-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e57fa-129">Odebrání <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce mění chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e57fa-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e57fa-130">Volání metody `Assert` nebo `Fail` metody obvykle za následek zobrazení okno se zprávou, ale do pole zpráva se nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e57fa-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e57fa-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="e57fa-131">Example</span></span>  
 <span data-ttu-id="e57fa-132">Následující příklad ukazuje, jak odebrat naslouchací proces trasování výchozí z trasování **naslouchací procesy** kolekce.</span><span class="sxs-lookup"><span data-stu-id="e57fa-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e57fa-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="e57fa-133">See Also</span></span>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [<span data-ttu-id="e57fa-134">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e57fa-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
