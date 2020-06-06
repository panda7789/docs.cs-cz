---
title: <remove>Element pro <listeners> pro<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153332"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="f94c2-102">\<remove>Element pro \<listeners> pro\<source></span><span class="sxs-lookup"><span data-stu-id="f94c2-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="f94c2-103">Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="f94c2-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="f94c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f94c2-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f94c2-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f94c2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f94c2-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f94c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f94c2-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f94c2-107">Attributes</span></span>  
  
|<span data-ttu-id="f94c2-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f94c2-108">Attribute</span></span>|<span data-ttu-id="f94c2-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f94c2-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f94c2-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f94c2-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="f94c2-111">Název naslouchacího procesu, který se má odebrat z `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="f94c2-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f94c2-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f94c2-112">Child Elements</span></span>  
 <span data-ttu-id="f94c2-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="f94c2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f94c2-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f94c2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f94c2-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="f94c2-115">Element</span></span>|<span data-ttu-id="f94c2-116">Description</span><span class="sxs-lookup"><span data-stu-id="f94c2-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f94c2-117">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f94c2-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f94c2-118">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="f94c2-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="f94c2-119">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="f94c2-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="f94c2-120">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="f94c2-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="f94c2-121">Určuje naslouchací procesy, které shromažďují, ukládají a směrují zprávy.</span><span class="sxs-lookup"><span data-stu-id="f94c2-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f94c2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f94c2-122">Remarks</span></span>  
 <span data-ttu-id="f94c2-123">`<remove>`Element Odebere zadaný naslouchací proces z `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="f94c2-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="f94c2-124">Můžete odebrat prvek z `Listeners` kolekce pro zdroj trasování programově voláním <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metody u <xref:System.Diagnostics.TraceSource.Listeners%2A> vlastnosti <xref:System.Diagnostics.TraceSource> instance.</span><span class="sxs-lookup"><span data-stu-id="f94c2-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="f94c2-125">Tento element lze použít v konfiguračním souboru počítače (Machine. config) a v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f94c2-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f94c2-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="f94c2-126">Example</span></span>  
 <span data-ttu-id="f94c2-127">Následující příklad ukazuje, jak použít `<remove>` element před použitím `<add>` elementu pro přidání naslouchacího procesu `console` do `Listeners` kolekce pro zdroj trasování `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="f94c2-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f94c2-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="f94c2-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="f94c2-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="f94c2-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="f94c2-130">Moduly naslouchání trasování</span><span class="sxs-lookup"><span data-stu-id="f94c2-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
