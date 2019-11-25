---
title: <remove> element pro <listeners> pro <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088834"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="09896-102">\<odebrat > elementu pro \<naslouchací proces > pro \<trace ></span><span class="sxs-lookup"><span data-stu-id="09896-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="09896-103">Odebere naslouchací proces z kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="09896-103">Removes a listener from the **Listeners** collection.</span></span>  

<span data-ttu-id="09896-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="09896-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="09896-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="09896-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="09896-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trace >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="09896-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="09896-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<naslouchacího procesu >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="09896-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="09896-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<odebrat >**</span><span class="sxs-lookup"><span data-stu-id="09896-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="09896-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09896-109">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09896-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="09896-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09896-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="09896-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09896-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="09896-112">Attributes</span></span>  
  
|<span data-ttu-id="09896-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="09896-113">Attribute</span></span>|<span data-ttu-id="09896-114">Popis</span><span class="sxs-lookup"><span data-stu-id="09896-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09896-115">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="09896-115">**name**</span></span>|<span data-ttu-id="09896-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="09896-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="09896-117">Název naslouchacího procesu, který se má odebrat z kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="09896-117">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09896-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="09896-118">Child Elements</span></span>  
 <span data-ttu-id="09896-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="09896-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09896-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="09896-120">Parent Elements</span></span>  
  
|<span data-ttu-id="09896-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="09896-121">Element</span></span>|<span data-ttu-id="09896-122">Popis</span><span class="sxs-lookup"><span data-stu-id="09896-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="09896-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09896-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="09896-124">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="09896-124">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="09896-125">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="09896-125">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="09896-126">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="09896-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="09896-127">Konfiguruje službu trasování ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="09896-127">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09896-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="09896-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09896-129">Odebráním <xref:System.Diagnostics.DefaultTraceListener> z kolekce `Listeners` se změní chování metod <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09896-129">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="09896-130">Volání metody `Assert` nebo `Fail` obvykle vede k zobrazení okna se zprávou, ale okno se zprávou není zobrazeno, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` Collection.</span><span class="sxs-lookup"><span data-stu-id="09896-130">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09896-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="09896-131">Example</span></span>  
 <span data-ttu-id="09896-132">Následující příklad ukazuje, jak odebrat výchozí naslouchací proces trasování z kolekce **posluchačů** trasování.</span><span class="sxs-lookup"><span data-stu-id="09896-132">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09896-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09896-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="09896-134">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="09896-134">Trace and Debug Settings Schema</span></span>](index.md)
