---
title: Element <alwaysFlowImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy
helpviewer_keywords:
- alwaysFlowImpersonationPolicy element
- <alwaysFlowImpersonationPolicy> element
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 164492eb1abc7329481f158963118b47d2c4aebc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252866"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="3ea4e-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="3ea4e-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="3ea4e-103">Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="3ea4e-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3ea4e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3ea4e-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="3ea4e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3ea4e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<alwaysFlowImpersonationPolicy>** </span><span class="sxs-lookup"><span data-stu-id="3ea4e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="3ea4e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ea4e-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ea4e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ea4e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3ea4e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ea4e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ea4e-110">Attributes</span></span>  
  
|<span data-ttu-id="3ea4e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ea4e-111">Attribute</span></span>|<span data-ttu-id="3ea4e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea4e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3ea4e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ea4e-114">Určuje, zda se v rámci asynchronních bodů využívá identita systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3ea4e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="3ea4e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3ea4e-116">Value</span><span class="sxs-lookup"><span data-stu-id="3ea4e-116">Value</span></span>|<span data-ttu-id="3ea4e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea4e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3ea4e-118">Identita systému Windows není předávána mezi asynchronními body, pokud zosobnění není provedeno prostřednictvím spravovaných metod <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>, jako je.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="3ea4e-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="3ea4e-120">Identita systému Windows vždy přetéká napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ea4e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea4e-121">Child Elements</span></span>  
 <span data-ttu-id="3ea4e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ea4e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ea4e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ea4e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3ea4e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ea4e-124">Element</span></span>|<span data-ttu-id="3ea4e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3ea4e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3ea4e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3ea4e-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea4e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ea4e-128">Remarks</span></span>  
 <span data-ttu-id="3ea4e-129">V .NET Framework verzích 1,0 a 1,1 neprovádí identita systému Windows tok mezi asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="3ea4e-130">V .NET Framework verze 2,0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně vykonávajícím vlákně a přenáší je napříč asynchronními body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="3ea4e-131">Také <xref:System.Security.Principal.WindowsIdentity> se přenáší jako součást informací, které jsou v průběhu asynchronních bodů za předpokladu, že došlo k zosobnění pomocí spravovaných <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> metod, jako je a nikoli prostřednictvím jiných prostředků, jako je vyvolání platformy pro nativní metody.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="3ea4e-132">Tento prvek slouží k určení toho, že identita systému Windows probíhá přes asynchronní body bez ohledu na to, jakým způsobem bylo dosaženo zosobnění.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="3ea4e-133">Výchozí chování můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="3ea4e-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="3ea4e-134">Ve spravovaném kódu v závislosti na vlákně.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="3ea4e-135">Tok můžete <xref:System.Threading.ExecutionContext> potlačit na základě jednotlivých vláken úpravou nastavení a <xref:System.Security.SecurityContext> pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3ea4e-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="3ea4e-136">Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="3ea4e-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="3ea4e-137">Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="3ea4e-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="3ea4e-138">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na. `STARTUP_ALWAYSFLOW_IMPERSONATION`</span><span class="sxs-lookup"><span data-stu-id="3ea4e-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="3ea4e-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="3ea4e-139">Configuration File</span></span>  
 <span data-ttu-id="3ea4e-140">V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="3ea4e-141">V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který se nachází ve \<složce Windows > adresáři \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="3ea4e-142">ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru ASPNET. config pomocí následujících nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="3ea4e-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="3ea4e-143">Pokud chcete místo toho použít tok zosobnění, musíte v ASP.NET explicitně použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="3ea4e-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="3ea4e-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ea4e-144">Example</span></span>  
 <span data-ttu-id="3ea4e-145">Následující příklad ukazuje, jak určit, že se má identita systému Windows provádět napříč asynchronními body, a to i v případě, že je možné zosobnění dosáhnout prostřednictvím jiných prostředků než spravovaných metod.</span><span class="sxs-lookup"><span data-stu-id="3ea4e-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ea4e-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ea4e-146">See also</span></span>

- [<span data-ttu-id="3ea4e-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="3ea4e-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3ea4e-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3ea4e-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3ea4e-149">\<legacyImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="3ea4e-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
