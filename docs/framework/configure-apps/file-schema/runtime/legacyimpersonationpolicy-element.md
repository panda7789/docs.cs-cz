---
title: Element <legacyImpersonationPolicy>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy
helpviewer_keywords:
- <legacyImpersonationPolicy> element
- legacyImpersonationPolicy element
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cf997c8ff13e0a6a4664ea3b538ac0def1baacf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663630"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="eba71-102">\<legacyImpersonationPolicy – element ></span><span class="sxs-lookup"><span data-stu-id="eba71-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="eba71-103">Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="eba71-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="eba71-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="eba71-104">\<configuration></span></span>  
<span data-ttu-id="eba71-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="eba71-105">\<runtime></span></span>  
<span data-ttu-id="eba71-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="eba71-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eba71-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eba71-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eba71-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eba71-108">Attributes and Elements</span></span>  
 <span data-ttu-id="eba71-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eba71-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eba71-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="eba71-110">Attributes</span></span>  
  
|<span data-ttu-id="eba71-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="eba71-111">Attribute</span></span>|<span data-ttu-id="eba71-112">Popis</span><span class="sxs-lookup"><span data-stu-id="eba71-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="eba71-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="eba71-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="eba71-114">Určuje, že <xref:System.Security.Principal.WindowsIdentity> nedojde k toku mezi asynchronními body bez ohledu na <xref:System.Threading.ExecutionContext> nastavení toku v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="eba71-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="eba71-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="eba71-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="eba71-116">Value</span><span class="sxs-lookup"><span data-stu-id="eba71-116">Value</span></span>|<span data-ttu-id="eba71-117">Popis</span><span class="sxs-lookup"><span data-stu-id="eba71-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="eba71-118"><xref:System.Security.Principal.WindowsIdentity>toky napříč asynchronními body v závislosti <xref:System.Threading.ExecutionContext> na nastavení toku pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="eba71-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="eba71-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="eba71-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="eba71-120"><xref:System.Security.Principal.WindowsIdentity>neprovádí tok mezi asynchronními body bez ohledu na <xref:System.Threading.ExecutionContext> nastavení toku v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="eba71-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eba71-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eba71-121">Child Elements</span></span>  
 <span data-ttu-id="eba71-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="eba71-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eba71-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eba71-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eba71-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="eba71-124">Element</span></span>|<span data-ttu-id="eba71-125">Popis</span><span class="sxs-lookup"><span data-stu-id="eba71-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="eba71-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eba71-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="eba71-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="eba71-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba71-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eba71-128">Remarks</span></span>  
 <span data-ttu-id="eba71-129">V .NET Framework verzích 1,0 a 1,1 <xref:System.Security.Principal.WindowsIdentity> není tok rozložen mezi žádné uživatelem definované asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="eba71-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="eba71-130">.NET Framework počínaje verzí 2,0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně zpracovávaném vlákně a který je v rámci domény aplikace tok mezi asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="eba71-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="eba71-131"><xref:System.Security.Principal.WindowsIdentity> Je součástí tohoto kontextu spuštění, a proto také toků napříč asynchronními body, což znamená, že pokud existuje kontext zosobnění, bude tok také.</span><span class="sxs-lookup"><span data-stu-id="eba71-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="eba71-132">Počínaje .NET Framework 2,0 můžete použít `<legacyImpersonationPolicy>` element k určení, které <xref:System.Security.Principal.WindowsIdentity> není v rámci asynchronních bodů natéká.</span><span class="sxs-lookup"><span data-stu-id="eba71-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eba71-133">Modul CLR (Common Language Runtime) ví o operacích zosobnění provedených pomocí pouze spravovaného kódu, nikoli zosobnění prováděné mimo spravovaný kód, jako je například volání platformy do nespravovaného kódu nebo prostřednictvím přímých volání funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="eba71-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="eba71-134">Pouze spravované <xref:System.Security.Principal.WindowsIdentity> objekty mohou procházet přes asynchronní body, `alwaysFlowImpersonationPolicy` Pokud prvek nebyl nastaven na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="eba71-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="eba71-135">`alwaysFlowImpersonationPolicy` Nastavení elementu na hodnotu true Určuje, že identita systému Windows je vždy přenášena přes asynchronní body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="eba71-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="eba71-136">Další informace o tom, jak přesměrovat nespravované zosobnění přes asynchronní body, naleznete v tématu [ \<alwaysFlowImpersonationPolicy > element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="eba71-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="eba71-137">Výchozí chování můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="eba71-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="eba71-138">Ve spravovaném kódu v závislosti na vlákně.</span><span class="sxs-lookup"><span data-stu-id="eba71-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="eba71-139">Tok <xref:System.Threading.ExecutionContext> můžete potlačit na základě jednotlivých vláken úpravou <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nastavení a <xref:System.Security.SecurityContext> pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>metody nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="eba71-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="eba71-140">Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="eba71-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="eba71-141">Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="eba71-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="eba71-142">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="eba71-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="eba71-143">Další informace naleznete v [ \<tématu alwaysFlowImpersonationPolicy > element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="eba71-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="eba71-144">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="eba71-144">Configuration File</span></span>  
 <span data-ttu-id="eba71-145">V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="eba71-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="eba71-146">V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který se nachází ve \<složce Windows > adresáři \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="eba71-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="eba71-147">ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru ASPNET. config pomocí následujících nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="eba71-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="eba71-148">Pokud chcete místo toho použít tok zosobnění, musíte v ASP.NET explicitně použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="eba71-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="eba71-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="eba71-149">Example</span></span>  
 <span data-ttu-id="eba71-150">Následující příklad ukazuje, jak určit starší chování, které neflowuje identitu systému Windows napříč asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="eba71-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eba71-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eba71-151">See also</span></span>

- [<span data-ttu-id="eba71-152">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="eba71-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="eba71-153">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="eba71-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eba71-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="eba71-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
