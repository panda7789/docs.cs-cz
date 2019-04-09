---
title: <remove> – Element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: adf00394bc0bfe808836e74214003cd2078204e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164252"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="c9f4e-102">\<Odebrat > – Element pro \<naslouchacích procesů > pro \<trasování ></span><span class="sxs-lookup"><span data-stu-id="c9f4e-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="c9f4e-103">Odebere z naslouchacího procesu **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-103">Removes a listener from the **Listeners** collection.</span></span>  
  
 <span data-ttu-id="c9f4e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c9f4e-104">\<configuration></span></span>  
<span data-ttu-id="c9f4e-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c9f4e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c9f4e-106">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="c9f4e-106">\<trace></span></span>  
<span data-ttu-id="c9f4e-107">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="c9f4e-107">\<listeners></span></span>  
<span data-ttu-id="c9f4e-108">\<remove></span><span class="sxs-lookup"><span data-stu-id="c9f4e-108">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f4e-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9f4e-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9f4e-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9f4e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c9f4e-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9f4e-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9f4e-112">Attributes</span></span>  
  
|<span data-ttu-id="c9f4e-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c9f4e-113">Attribute</span></span>|<span data-ttu-id="c9f4e-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c9f4e-114">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="c9f4e-115">name</span><span class="sxs-lookup"><span data-stu-id="c9f4e-115">name</span></span>**|<span data-ttu-id="c9f4e-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9f4e-117">Název naslouchacího procesu odebrání **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9f4e-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9f4e-118">Child Elements</span></span>  
 <span data-ttu-id="c9f4e-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9f4e-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9f4e-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9f4e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c9f4e-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9f4e-121">Element</span></span>|<span data-ttu-id="c9f4e-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c9f4e-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9f4e-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="c9f4e-124">Určuje naslouchací proces, který shromažďuje, ukládá a provádí směrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="c9f4e-125">Posluchači přímý výstup trasování příslušný cíli.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c9f4e-126">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="c9f4e-127">Nakonfiguruje službu sledování technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9f4e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9f4e-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9f4e-129">Odebírá <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce mění chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="c9f4e-130">Volání `Assert` nebo `Fail` metoda normálně ve výsledku zobrazení okna se zprávou, ale okno se zprávou se nezobrazí, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9f4e-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9f4e-131">Example</span></span>  
 <span data-ttu-id="c9f4e-132">Následující příklad ukazuje, jak k odebrání naslouchacího procesu trasování výchozí trasování **naslouchacích procesů** kolekce.</span><span class="sxs-lookup"><span data-stu-id="c9f4e-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c9f4e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9f4e-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="c9f4e-134">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c9f4e-134">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
