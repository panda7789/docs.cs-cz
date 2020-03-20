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
ms.openlocfilehash: 5e43ead278ecd4049014f4000a2f056b2190f7e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154101"
---
# <a name="legacyimpersonationpolicy-element"></a><span data-ttu-id="1bd0e-102">\<starší verze ImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="1bd0e-102">\<legacyImpersonationPolicy> Element</span></span>
<span data-ttu-id="1bd0e-103">Určuje, že identita systému Windows neprobíhá přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
<span data-ttu-id="1bd0e-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1bd0e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1bd0e-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1bd0e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="1bd0e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<starší>verze**</span><span class="sxs-lookup"><span data-stu-id="1bd0e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyImpersonationPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd0e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bd0e-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1bd0e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1bd0e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1bd0e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1bd0e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1bd0e-110">Attributes</span></span>  
  
|<span data-ttu-id="1bd0e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1bd0e-111">Attribute</span></span>|<span data-ttu-id="1bd0e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1bd0e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="1bd0e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="1bd0e-114">Určuje, že <xref:System.Security.Principal.WindowsIdentity> netokuje přes asynchronní body, <xref:System.Threading.ExecutionContext> bez ohledu na nastavení toku v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1bd0e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="1bd0e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="1bd0e-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1bd0e-116">Value</span></span>|<span data-ttu-id="1bd0e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1bd0e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="1bd0e-118"><xref:System.Security.Principal.WindowsIdentity>toky přes asynchronní body <xref:System.Threading.ExecutionContext> v závislosti na nastavení toku pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="1bd0e-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="1bd0e-120"><xref:System.Security.Principal.WindowsIdentity>netokuje přes asynchronní body, <xref:System.Threading.ExecutionContext> bez ohledu na nastavení toku v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1bd0e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1bd0e-121">Child Elements</span></span>  
 <span data-ttu-id="1bd0e-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1bd0e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1bd0e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1bd0e-124">Element</span><span class="sxs-lookup"><span data-stu-id="1bd0e-124">Element</span></span>|<span data-ttu-id="1bd0e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1bd0e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1bd0e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1bd0e-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd0e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bd0e-128">Remarks</span></span>  
 <span data-ttu-id="1bd0e-129">V rozhraní .NET Framework verze 1.0 a <xref:System.Security.Principal.WindowsIdentity> 1.1 netokuje přes všechny uživatelem definované asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="1bd0e-130">Počínaje rozhraním .NET Framework verze 2.0 existuje <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěném vlákně a toky přes asynchronní body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="1bd0e-131">Je <xref:System.Security.Principal.WindowsIdentity> součástí tohoto kontextu spuštění a proto také toky přes asynchronní body, což znamená, že pokud existuje kontext zosobnění, bude tok také.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="1bd0e-132">Počínaje rozhraním .NET Framework 2.0 `<legacyImpersonationPolicy>` můžete pomocí <xref:System.Security.Principal.WindowsIdentity> prvku určit, že neprobíhá přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bd0e-133">Clr (COMMON Language runtime) si je vědoma operací zosobnění prováděných pouze pomocí spravovaného kódu, nikoli zosobnění prováděného mimo spravovaný kód, například prostřednictvím vyvolání platformy k nespravovanému kódu nebo prostřednictvím přímých volání funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="1bd0e-134">Pouze <xref:System.Security.Principal.WindowsIdentity> spravované objekty mohou proudit přes `alwaysFlowImpersonationPolicy` asynchronní body,`<alwaysFlowImpersonationPolicy enabled="true"/>`pokud prvek nebyl nastaven na hodnotu true ( ).</span><span class="sxs-lookup"><span data-stu-id="1bd0e-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="1bd0e-135">Nastavení `alwaysFlowImpersonationPolicy` prvku na hodnotu true určuje, že identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="1bd0e-136">Další informace o plynulém nespravovaném zosobnění mezi asynchronními body naleznete v tématu [ \<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="1bd0e-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="1bd0e-137">Toto výchozí chování můžete změnit dvěma dalšími způsoby:</span><span class="sxs-lookup"><span data-stu-id="1bd0e-137">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="1bd0e-138">Ve spravovaném kódu pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="1bd0e-139">Tok můžete potlačit na základě vlákno úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> a nastavení <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>pomocí <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> , nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="1bd0e-140">Při volání nespravovaného hostitelského rozhraní načíst modul CLR (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="1bd0e-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="1bd0e-141">Pokud nespravované hostitelské rozhraní (namísto jednoduchého spravovaného spustitelného souboru) se používá k načtení CLR, můžete zadat speciální příznak ve volání [funkce CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="1bd0e-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="1bd0e-142">Chcete-li povolit režim kompatibility `flags` pro celý proces, nastavte parametr [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="1bd0e-143">Další informace naleznete [ \<v tématu alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="1bd0e-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="1bd0e-144">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="1bd0e-144">Configuration File</span></span>  
 <span data-ttu-id="1bd0e-145">V aplikaci rozhraní .NET Framework lze tento prvek použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="1bd0e-146">Pro ASP.NET aplikaci lze tok zosobnění nakonfigurovat v souboru aspnet.config, který se nachází v \<adresáři Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="1bd0e-147">ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru aspnet.config pomocí následujících nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="1bd0e-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="1bd0e-148">V ASP.NET, pokud chcete povolit tok zosobnění místo, musíte explicitně použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="1bd0e-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="1bd0e-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bd0e-149">Example</span></span>  
 <span data-ttu-id="1bd0e-150">Následující příklad ukazuje, jak určit starší chování, které netokuje identitu systému Windows přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="1bd0e-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bd0e-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bd0e-151">See also</span></span>

- [<span data-ttu-id="1bd0e-152">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="1bd0e-152">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="1bd0e-153">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1bd0e-153">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="1bd0e-154">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="1bd0e-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](alwaysflowimpersonationpolicy-element.md)
