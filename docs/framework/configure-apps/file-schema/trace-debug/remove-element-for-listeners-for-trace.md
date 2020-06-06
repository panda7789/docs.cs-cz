---
title: <remove>Element pro <listeners> pro<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: f06973ec30d5061e4a200d6bf7e68adcf6302018
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088834"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="74bfa-102">\<remove>Element pro \<listeners> pro\<trace></span><span class="sxs-lookup"><span data-stu-id="74bfa-102">\<remove> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="74bfa-103">Odebere naslouchací proces z kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="74bfa-103">Removes a listener from the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="74bfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74bfa-104">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74bfa-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74bfa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="74bfa-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74bfa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74bfa-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="74bfa-107">Attributes</span></span>  
  
|<span data-ttu-id="74bfa-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="74bfa-108">Attribute</span></span>|<span data-ttu-id="74bfa-109">Popis</span><span class="sxs-lookup"><span data-stu-id="74bfa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74bfa-110">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="74bfa-110">**name**</span></span>|<span data-ttu-id="74bfa-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="74bfa-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="74bfa-112">Název naslouchacího procesu, který se má odebrat z kolekce **posluchačů** .</span><span class="sxs-lookup"><span data-stu-id="74bfa-112">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74bfa-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74bfa-113">Child Elements</span></span>  
 <span data-ttu-id="74bfa-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="74bfa-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74bfa-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74bfa-115">Parent Elements</span></span>  
  
|<span data-ttu-id="74bfa-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="74bfa-116">Element</span></span>|<span data-ttu-id="74bfa-117">Description</span><span class="sxs-lookup"><span data-stu-id="74bfa-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="74bfa-118">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="74bfa-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="74bfa-119">Určuje naslouchací proces, který shromažďuje, ukládá a směruje zprávy.</span><span class="sxs-lookup"><span data-stu-id="74bfa-119">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="74bfa-120">Naslouchací procesy směrují výstup trasování do příslušného cíle.</span><span class="sxs-lookup"><span data-stu-id="74bfa-120">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="74bfa-121">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="74bfa-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="74bfa-122">Konfiguruje službu trasování ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="74bfa-122">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74bfa-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74bfa-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74bfa-124">Odebrání <xref:System.Diagnostics.DefaultTraceListener> z `Listeners` kolekce změní chování <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metod,, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> a <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74bfa-124">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="74bfa-125">Volání `Assert` metody nebo `Fail` obvykle vede k zobrazení okna se zprávou, avšak okno se zprávou není zobrazeno, pokud <xref:System.Diagnostics.DefaultTraceListener> není v `Listeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="74bfa-125">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74bfa-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="74bfa-126">Example</span></span>  
 <span data-ttu-id="74bfa-127">Následující příklad ukazuje, jak odebrat výchozí naslouchací proces trasování z kolekce **posluchačů** trasování.</span><span class="sxs-lookup"><span data-stu-id="74bfa-127">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="74bfa-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="74bfa-128">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="74bfa-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="74bfa-129">Trace and Debug Settings Schema</span></span>](index.md)
