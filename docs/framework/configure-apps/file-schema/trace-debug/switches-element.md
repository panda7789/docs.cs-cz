---
title: Element <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: 15cc9680d7a20341eb5d1d1df302c1e034e70e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153227"
---
# <a name="switches-element"></a><span data-ttu-id="726fb-102">\<přepínače> Element</span><span class="sxs-lookup"><span data-stu-id="726fb-102">\<switches> Element</span></span>
<span data-ttu-id="726fb-103">Obsahuje přepínače trasování a úroveň, kde jsou přepínače trasování nastaveny.</span><span class="sxs-lookup"><span data-stu-id="726fb-103">Contains trace switches and the level where the trace switches are set.</span></span>  

<span data-ttu-id="726fb-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="726fb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="726fb-105">&nbsp;&nbsp;[**\<system.diagnostická>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="726fb-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="726fb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<přepínače>**</span><span class="sxs-lookup"><span data-stu-id="726fb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**</span></span>

## <a name="syntax"></a><span data-ttu-id="726fb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="726fb-107">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="726fb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="726fb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="726fb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="726fb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="726fb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="726fb-110">Attributes</span></span>  
 <span data-ttu-id="726fb-111">Žádné.</span><span class="sxs-lookup"><span data-stu-id="726fb-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="726fb-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="726fb-112">Child Elements</span></span>  
  
|<span data-ttu-id="726fb-113">Element</span><span class="sxs-lookup"><span data-stu-id="726fb-113">Element</span></span>|<span data-ttu-id="726fb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="726fb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="726fb-115">\<přidat></span><span class="sxs-lookup"><span data-stu-id="726fb-115">\<add></span></span>](add-element-for-switches.md)|<span data-ttu-id="726fb-116">Určuje úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="726fb-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="726fb-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="726fb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="726fb-118">Element</span><span class="sxs-lookup"><span data-stu-id="726fb-118">Element</span></span>|<span data-ttu-id="726fb-119">Popis</span><span class="sxs-lookup"><span data-stu-id="726fb-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="726fb-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="726fb-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="726fb-121">Určuje posluchače trasování, které shromažďují, ukládají a směrují zprávy, a úroveň, na které je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="726fb-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="726fb-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="726fb-122">Remarks</span></span>  
 <span data-ttu-id="726fb-123">Úroveň trasovacího přepínače můžete změnit jeho vložením do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="726fb-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="726fb-124">Pokud je přepínač <xref:System.Diagnostics.BooleanSwitch>, můžete jej zapínat a vypínat.</span><span class="sxs-lookup"><span data-stu-id="726fb-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="726fb-125">Pokud je přepínač <xref:System.Diagnostics.TraceSwitch>, můžete mu přiřadit různé úrovně a určit typy trasovacích nebo ladicích zpráv, které aplikace vypíše.</span><span class="sxs-lookup"><span data-stu-id="726fb-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="726fb-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="726fb-126">Example</span></span>  
 <span data-ttu-id="726fb-127">Následující příklad ukazuje, jak pomocí \*\* \<prvku switch>\*\* nastavit <xref:System.Diagnostics.TraceLevel> přepínač `General` trasování `Data` na úroveň a povolit přepínač trasování logické.</span><span class="sxs-lookup"><span data-stu-id="726fb-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="726fb-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="726fb-128">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="726fb-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="726fb-129">Trace and Debug Settings Schema</span></span>](index.md)
