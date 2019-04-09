---
title: <remove> – Element pro <listeners> pro <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 4809c471deb51e0560b438b5a2c8849daad34ca0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120130"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="c2aba-102">\<Odebrat > – Element pro \<naslouchacích procesů > pro \<zdroje ></span><span class="sxs-lookup"><span data-stu-id="c2aba-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="c2aba-103">Odebere z naslouchacího procesu `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="c2aba-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="c2aba-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c2aba-104">\<configuration></span></span>  
<span data-ttu-id="c2aba-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="c2aba-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c2aba-106">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="c2aba-106">\<sources></span></span>  
<span data-ttu-id="c2aba-107">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="c2aba-107">\<source></span></span>  
<span data-ttu-id="c2aba-108">\<naslouchací procesy ></span><span class="sxs-lookup"><span data-stu-id="c2aba-108">\<listeners></span></span>  
<span data-ttu-id="c2aba-109">\<remove></span><span class="sxs-lookup"><span data-stu-id="c2aba-109">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2aba-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2aba-110">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2aba-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2aba-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c2aba-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2aba-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2aba-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2aba-113">Attributes</span></span>  
  
|<span data-ttu-id="c2aba-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2aba-114">Attribute</span></span>|<span data-ttu-id="c2aba-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c2aba-115">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="c2aba-116">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c2aba-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="c2aba-117">Název naslouchacího procesu odebrání `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="c2aba-117">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2aba-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2aba-118">Child Elements</span></span>  
 <span data-ttu-id="c2aba-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="c2aba-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2aba-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2aba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c2aba-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2aba-121">Element</span></span>|<span data-ttu-id="c2aba-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c2aba-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c2aba-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2aba-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c2aba-124">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="c2aba-124">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="c2aba-125">Obsahuje zdrojů trasování, které se zahájí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="c2aba-125">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="c2aba-126">Určuje zdroj trasování, který iniciuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="c2aba-126">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="c2aba-127">Určuje naslouchací procesy, které shromažďování, ukládání a směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="c2aba-127">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2aba-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2aba-128">Remarks</span></span>  
 <span data-ttu-id="c2aba-129">`<remove>` Element Odebere zadaný naslouchací proces z `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="c2aba-129">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="c2aba-130">Odebrat element z `Listeners` kolekce pro zdroj trasování programově zavoláním <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodu na <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnost <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="c2aba-130">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="c2aba-131">Tento element lze použít v konfiguračním souboru počítače (Machine.config) a konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2aba-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2aba-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2aba-132">Example</span></span>  
 <span data-ttu-id="c2aba-133">Následující příklad ukazuje způsob použití `<remove>` prvek před použitím `<add>` prvek a přidat naslouchací proces `console` k `Listeners` kolekce pro zdroj trasování `TraceSourceApp`.</span><span class="sxs-lookup"><span data-stu-id="c2aba-133">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2aba-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2aba-134">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="c2aba-135">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="c2aba-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="c2aba-136">\<clear></span><span class="sxs-lookup"><span data-stu-id="c2aba-136">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="c2aba-137">Naslouchací procesy trasování</span><span class="sxs-lookup"><span data-stu-id="c2aba-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
