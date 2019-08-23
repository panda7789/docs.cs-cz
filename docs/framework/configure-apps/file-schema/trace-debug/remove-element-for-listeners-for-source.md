---
title: <remove>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: edd27dd262004aead7db4d81db8ecab0e831dac1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926996"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="d51d2-102">\<Odebrat element > pro \<naslouchací procesy > \<pro > zdrojového kódu</span><span class="sxs-lookup"><span data-stu-id="d51d2-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="d51d2-103">Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="d51d2-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="d51d2-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d51d2-104">\<configuration></span></span>  
<span data-ttu-id="d51d2-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="d51d2-105">\<system.diagnostics></span></span>  
<span data-ttu-id="d51d2-106">\<> zdrojů</span><span class="sxs-lookup"><span data-stu-id="d51d2-106">\<sources></span></span>  
<span data-ttu-id="d51d2-107">\<> zdroje</span><span class="sxs-lookup"><span data-stu-id="d51d2-107">\<source></span></span>  
<span data-ttu-id="d51d2-108">\<> naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="d51d2-108">\<listeners></span></span>  
<span data-ttu-id="d51d2-109">\<odebrat ></span><span class="sxs-lookup"><span data-stu-id="d51d2-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d51d2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d51d2-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d51d2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d51d2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d51d2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d51d2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d51d2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d51d2-113">Attributes</span></span>  
  
|<span data-ttu-id="d51d2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d51d2-114">Attribute</span></span>|<span data-ttu-id="d51d2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d51d2-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d51d2-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d51d2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="d51d2-117">Název naslouchacího procesu, který se má odebrat z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="d51d2-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d51d2-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d51d2-118">Child Elements</span></span>  
 <span data-ttu-id="d51d2-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="d51d2-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d51d2-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d51d2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d51d2-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d51d2-121">Element</span></span>|<span data-ttu-id="d51d2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d51d2-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d51d2-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d51d2-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d51d2-124">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="d51d2-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d51d2-125">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d51d2-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d51d2-126">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="d51d2-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d51d2-127">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="d51d2-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d51d2-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d51d2-128">Remarks</span></span>  
 <span data-ttu-id="d51d2-129">Element Odebere zadaný naslouchací proces `Listeners` z kolekce pro zdroj trasování. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="d51d2-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="d51d2-130">Můžete `Listeners` odebrat prvek z kolekce pro zdroj trasování programově <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> voláním metody <xref:System.Diagnostics.TraceSource> u <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="d51d2-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="d51d2-131">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d51d2-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51d2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d51d2-132">Example</span></span>  
 <span data-ttu-id="d51d2-133">Následující příklad `<remove>` ukazuje, jak použít element před `<add>` použitím elementu pro `Listeners` přidání naslouchacího procesu `console` do kolekce pro zdroj `TraceSourceApp`trasování.</span><span class="sxs-lookup"><span data-stu-id="d51d2-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"   
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="d51d2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d51d2-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="d51d2-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="d51d2-135">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d51d2-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="d51d2-136">\<clear></span></span>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="d51d2-137">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="d51d2-137">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
