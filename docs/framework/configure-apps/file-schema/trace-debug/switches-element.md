---
title: '&lt;přepínače&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: ed5d30408b2c0f45f3bef091f4828bd812a63a7a
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083350"
---
# <a name="ltswitchesgt-element"></a><span data-ttu-id="8d4cf-102">&lt;přepínače&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="8d4cf-102">&lt;switches&gt; Element</span></span>
<span data-ttu-id="8d4cf-103">Obsahuje přepínače trasování a úrovně, ve kterém jsou nastavené přepínačů trasování.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-103">Contains trace switches and the level where the trace switches are set.</span></span>  
  
 <span data-ttu-id="8d4cf-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="8d4cf-104">\<configuration></span></span>  
<span data-ttu-id="8d4cf-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="8d4cf-105">\<system.diagnostics></span></span>  
<span data-ttu-id="8d4cf-106">\<switches></span><span class="sxs-lookup"><span data-stu-id="8d4cf-106">\<switches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4cf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d4cf-107">Syntax</span></span>  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d4cf-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d4cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8d4cf-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d4cf-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d4cf-110">Attributes</span></span>  
 <span data-ttu-id="8d4cf-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d4cf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d4cf-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d4cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="8d4cf-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d4cf-113">Element</span></span>|<span data-ttu-id="8d4cf-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8d4cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d4cf-115">\<add></span><span class="sxs-lookup"><span data-stu-id="8d4cf-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="8d4cf-116">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-116">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d4cf-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d4cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8d4cf-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8d4cf-118">Element</span></span>|<span data-ttu-id="8d4cf-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8d4cf-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8d4cf-120">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="8d4cf-121">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d4cf-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d4cf-122">Remarks</span></span>  
 <span data-ttu-id="8d4cf-123">Úroveň trasování přepínače můžete změnit tak, že ji vložíte konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-123">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="8d4cf-124">Pokud je v přepínači <xref:System.Diagnostics.BooleanSwitch>, můžete ji zapnout a vypnout.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-124">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="8d4cf-125">Pokud je v přepínači <xref:System.Diagnostics.TraceSwitch>, můžete přiřadit různé úrovně možné určit typy trasování nebo zprávy ladění aplikace výstupy.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-125">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d4cf-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d4cf-126">Example</span></span>  
 <span data-ttu-id="8d4cf-127">Následující příklad ukazuje způsob použití  **\<přepnout >** – element pro nastavení `General` přepínačem trasování do <xref:System.Diagnostics.TraceLevel> úrovně a povolit `Data` trasování logický přepínač.</span><span class="sxs-lookup"><span data-stu-id="8d4cf-127">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d4cf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d4cf-128">See also</span></span>
- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="8d4cf-129">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="8d4cf-129">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
