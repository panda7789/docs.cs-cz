---
title: '&lt;legacyimpersonationpolicy –&gt; – Element'
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
ms.openlocfilehash: f90853a93b40eeb72f07ad9b1849aa99c8e8bf3d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745185"
---
# <a name="ltlegacyimpersonationpolicygt-element"></a><span data-ttu-id="58e5a-102">&lt;legacyimpersonationpolicy –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="58e5a-102">&lt;legacyImpersonationPolicy&gt; Element</span></span>
<span data-ttu-id="58e5a-103">Určuje, že identitu systému Windows není toku napříč asynchronní bodů, bez ohledu na nastavení tok pro kontext provádění na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="58e5a-103">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>  
  
 <span data-ttu-id="58e5a-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="58e5a-104">\<configuration></span></span>  
<span data-ttu-id="58e5a-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="58e5a-105">\<runtime></span></span>  
<span data-ttu-id="58e5a-106">\<legacyimpersonationpolicy – ></span><span class="sxs-lookup"><span data-stu-id="58e5a-106">\<legacyImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e5a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e5a-107">Syntax</span></span>  
  
```xml  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58e5a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="58e5a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="58e5a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="58e5a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58e5a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="58e5a-110">Attributes</span></span>  
  
|<span data-ttu-id="58e5a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="58e5a-111">Attribute</span></span>|<span data-ttu-id="58e5a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="58e5a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="58e5a-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="58e5a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="58e5a-114">Určuje, že <xref:System.Security.Principal.WindowsIdentity> nepostupuje napříč asynchronní bodů, bez ohledu na to <xref:System.Threading.ExecutionContext> toku nastavení na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="58e5a-114">Specifies that the <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="58e5a-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="58e5a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="58e5a-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="58e5a-116">Value</span></span>|<span data-ttu-id="58e5a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="58e5a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="58e5a-118"><xref:System.Security.Principal.WindowsIdentity> toky přes asynchronní body, v závislosti na <xref:System.Threading.ExecutionContext> toku nastavení pro aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="58e5a-118"><xref:System.Security.Principal.WindowsIdentity> flows across asynchronous points depending upon the <xref:System.Threading.ExecutionContext> flow settings for the current thread.</span></span> <span data-ttu-id="58e5a-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="58e5a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="58e5a-120"><xref:System.Security.Principal.WindowsIdentity> nepostupuje napříč asynchronní bodů, bez ohledu na to <xref:System.Threading.ExecutionContext> toku nastavení na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="58e5a-120"><xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points, regardless of the <xref:System.Threading.ExecutionContext> flow settings on the current thread.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58e5a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="58e5a-121">Child Elements</span></span>  
 <span data-ttu-id="58e5a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="58e5a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58e5a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="58e5a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58e5a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="58e5a-124">Element</span></span>|<span data-ttu-id="58e5a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="58e5a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="58e5a-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58e5a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="58e5a-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="58e5a-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58e5a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="58e5a-128">Remarks</span></span>  
 <span data-ttu-id="58e5a-129">V rozhraní .NET Framework verze 1.0 a 1.1 <xref:System.Security.Principal.WindowsIdentity> nepostupuje přes všechny body asynchronní definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="58e5a-129">In the .NET Framework versions 1.0 and 1.1, the <xref:System.Security.Principal.WindowsIdentity> does not flow across any user-defined asynchronous points.</span></span> <span data-ttu-id="58e5a-130">Od verze rozhraní .NET Framework verze 2.0, je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěném vlákno a toků mezi asynchronní body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="58e5a-130">Starting with the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and it flows across asynchronous points within an application domain.</span></span> <span data-ttu-id="58e5a-131"><xref:System.Security.Principal.WindowsIdentity> Je zahrnutý v tomto kontextu provádění a proto také toků mezi asynchronní body, což znamená, že pokud kontextu zosobnění existuje, ji budou směrovat také.</span><span class="sxs-lookup"><span data-stu-id="58e5a-131">The <xref:System.Security.Principal.WindowsIdentity> is included in this execution context and therefore also flows across the asynchronous points, which means that if an impersonation context exists, it will flow as well.</span></span>  
  
 <span data-ttu-id="58e5a-132">Od verze rozhraní .NET Framework 2.0, můžete použít `<legacyImpersonationPolicy>` elementu, který chcete určit, že <xref:System.Security.Principal.WindowsIdentity> nepostupuje přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="58e5a-132">Starting with the .NET Framework 2.0, you can use the `<legacyImpersonationPolicy>` element to specify that  <xref:System.Security.Principal.WindowsIdentity> does not flow across asynchronous points.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58e5a-133">Modul CLR (CLR) má informace o zosobnění operace provedené pomocí pouze spravovaného kódu, nikoli instanci zosobnění provést mimo spravovaného kódu, například prostřednictvím platformy volání nespravovaného kódu nebo prostřednictvím přímé volání funkcí Win32.</span><span class="sxs-lookup"><span data-stu-id="58e5a-133">The common language runtime (CLR) is aware of impersonation operations performed using only managed code, not of impersonation performed outside of managed code, such as through platform invoke to unmanaged code or through direct calls to Win32 functions.</span></span> <span data-ttu-id="58e5a-134">Jenom spravované <xref:System.Security.Principal.WindowsIdentity> objekty toku asynchronní body, pokud `alwaysFlowImpersonationPolicy` element byla nastavena na hodnotu true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span><span class="sxs-lookup"><span data-stu-id="58e5a-134">Only managed <xref:System.Security.Principal.WindowsIdentity> objects can flow across asynchronous points, unless the `alwaysFlowImpersonationPolicy` element has been set to true (`<alwaysFlowImpersonationPolicy enabled="true"/>`).</span></span> <span data-ttu-id="58e5a-135">Nastavení `alwaysFlowImpersonationPolicy` určuje element na hodnotu true, identitu systému Windows vždycky přeteče asynchronní bodů, bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="58e5a-135">Setting the `alwaysFlowImpersonationPolicy` element to true specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span> <span data-ttu-id="58e5a-136">Další informace o toku nespravované zosobnění přes asynchronní body najdete v tématu [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="58e5a-136">For more information on flowing unmanaged impersonation across asynchronous points, see [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
 <span data-ttu-id="58e5a-137">Chcete-li změnit toto výchozí chování v dva způsoby, jak:</span><span class="sxs-lookup"><span data-stu-id="58e5a-137">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="58e5a-138">Ve spravovaném kódu na základě vlákna.</span><span class="sxs-lookup"><span data-stu-id="58e5a-138">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="58e5a-139">Můžete potlačit toku na základě vlákna změnou <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="58e5a-139">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="58e5a-140">Ve volání rozhraní nespravované hostingu načíst modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="58e5a-140">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="58e5a-141">Pokud nespravované rozhraní hostování (namísto jednoduché spustitelný soubor spravovaných) se používá k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="58e5a-141">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="58e5a-142">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k STARTUP_LEGACY_IMPERSONATION.</span><span class="sxs-lookup"><span data-stu-id="58e5a-142">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to STARTUP_LEGACY_IMPERSONATION.</span></span>  
  
 <span data-ttu-id="58e5a-143">Další informace najdete v tématu [ \<alwaysflowimpersonationpolicy – > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span><span class="sxs-lookup"><span data-stu-id="58e5a-143">For more information, see the [\<alwaysFlowImpersonationPolicy> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md).</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="58e5a-144">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="58e5a-144">Configuration File</span></span>  
 <span data-ttu-id="58e5a-145">V aplikaci rozhraní .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="58e5a-145">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="58e5a-146">Pro aplikaci ASP.NET toku zosobnění lze konfigurovat v nalezen v souboru aspnet.config \<složka systému Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.</span><span class="sxs-lookup"><span data-stu-id="58e5a-146">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="58e5a-147">Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v souboru aspnet.config pomocí následujících nastavení:</span><span class="sxs-lookup"><span data-stu-id="58e5a-147">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
``` xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="58e5a-148">V technologii ASP.NET Pokud chcete povolit tok zosobnění místo toho je nutné explicitně zadat následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="58e5a-148">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="58e5a-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="58e5a-149">Example</span></span>  
 <span data-ttu-id="58e5a-150">Následující příklad ukazuje, jak určit způsob chování starší verze, který není toku identitu systému Windows přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="58e5a-150">The following example shows how to specify the legacy behavior that does not flow the Windows identity across asynchronous points.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58e5a-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="58e5a-151">See Also</span></span>  
 [<span data-ttu-id="58e5a-152">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="58e5a-152">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="58e5a-153">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="58e5a-153">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="58e5a-154">\<alwaysflowimpersonationpolicy – > elementu</span><span class="sxs-lookup"><span data-stu-id="58e5a-154">\<alwaysFlowImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)
