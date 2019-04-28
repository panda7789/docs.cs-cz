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
ms.openlocfilehash: c39ee551dde19d87a75403f3db7433d1ef829f3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704632"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="29219-102">\<legacyImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="29219-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="29219-103">Určuje, že identita Windows není téct přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="29219-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="29219-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="29219-104">\<configuration></span></span>  
<span data-ttu-id="29219-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="29219-105">\<runtime></span></span>  
<span data-ttu-id="29219-106">\<legacyImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="29219-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29219-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29219-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29219-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="29219-108">Attributes and Elements</span></span>  
 <span data-ttu-id="29219-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="29219-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29219-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="29219-110">Attributes</span></span>  
  
|<span data-ttu-id="29219-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="29219-111">Attribute</span></span>|<span data-ttu-id="29219-112">Popis</span><span class="sxs-lookup"><span data-stu-id="29219-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="29219-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="29219-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="29219-114">Určuje, že <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body, bez ohledu na to <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="29219-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="29219-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="29219-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="29219-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="29219-116">Value</span></span>|<span data-ttu-id="29219-117">Popis</span><span class="sxs-lookup"><span data-stu-id="29219-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="29219-118"><xref:System.Security.Principal.WindowsIdentity> toky přes asynchronní body v závislosti na <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="29219-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="29219-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="29219-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="29219-120"><xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body, bez ohledu <xref:System.Threading.ExecutionContext> tok nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="29219-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29219-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="29219-121">Child Elements</span></span>  
 <span data-ttu-id="29219-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="29219-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29219-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="29219-123">Parent Elements</span></span>  
  
|<span data-ttu-id="29219-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="29219-124">Element</span></span>|<span data-ttu-id="29219-125">Popis</span><span class="sxs-lookup"><span data-stu-id="29219-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="29219-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="29219-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="29219-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="29219-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29219-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29219-128">Remarks</span></span>  
 <span data-ttu-id="29219-129">V rozhraní .NET Framework verze 1.0 a 1.1 <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body žádné definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="29219-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="29219-130">Od verze rozhraní .NET Framework verze 2.0, je <xref:System.Threading.ExecutionContext> toků, který obsahuje informace o aktuálně spuštěné vlákno a to přes asynchronní body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="29219-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="29219-131"><xref:System.Security.Principal.WindowsIdentity> Je zahrnutá v tomto kontextu spuštění a proto se přenášejí také přes asynchronní body, což znamená, že pokud existuje objekt context zosobnění, se budou směrovat také.</span><span class="sxs-lookup"><span data-stu-id="29219-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="29219-132">Od verze rozhraní .NET Framework 2.0, můžete použít `<legacyImpersonationPolicy>` elementu, chcete-li určit, že <xref:System.Security.Principal.WindowsIdentity> není téct přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="29219-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29219-133">Modul CLR (CLR) je seznámen zosobnění operací provedených pomocí pouze spravovaný kód, ne o zosobnění provést mimo spravovaný kód, například prostřednictvím platformy volání nespravovaného kódu nebo prostřednictvím přímé volání funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="29219-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="29219-134">Pouze spravované <xref:System.Security.Principal.WindowsIdentity> objekty může téct přes asynchronní body, pokud `alwaysFlowImpersonationPolicy` prvku je nastavená na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="29219-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="29219-135">Nastavení `alwaysFlowImpersonationPolicy` prvku na hodnotu true Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.</span><span class="sxs-lookup"><span data-stu-id="29219-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="29219-136">Další informace o toku nespravované zosobnění přes asynchronní body, přečtěte si téma [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="29219-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="29219-137">Je-li změnit toto výchozí chování dvěma dalšími způsoby:</span><span class="sxs-lookup"><span data-stu-id="29219-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="29219-138">Ve spravovaném kódu na základě vlákno.</span><span class="sxs-lookup"><span data-stu-id="29219-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="29219-139">Tok na základě vlákna můžete potlačit pomocí úpravy <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="29219-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="29219-140">Ve volání nespravovaných hostitelských rozhraní načíst modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="29219-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="29219-141">Pokud nespravovaných hostitelských rozhraní (místo jednoduchých spustitelný soubor spravovaný) slouží k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="29219-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="29219-142">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="29219-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="29219-143">Další informace najdete v tématu [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="29219-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="29219-144">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="29219-144">Configuration File</span></span>  
 <span data-ttu-id="29219-145">V aplikaci .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="29219-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="29219-146">Pro aplikace ASP.NET se dá nakonfigurovat tok zosobnění v soubor aspnet.config součástí \<složky Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.</span><span class="sxs-lookup"><span data-stu-id="29219-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="29219-147">Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v soubor aspnet.config pomocí následujících nastavení:</span><span class="sxs-lookup"><span data-stu-id="29219-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="29219-148">V technologii ASP.NET Pokud chcete místo toho povolit tok zosobnění je nutné explicitně zadat následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="29219-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="29219-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="29219-149">Example</span></span>  
 <span data-ttu-id="29219-150">Následující příklad ukazuje, jak určit starší chování, které není identita Windows téct přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="29219-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29219-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29219-151">See also</span></span>

- [<span data-ttu-id="29219-152">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="29219-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="29219-153">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="29219-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="29219-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="29219-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
