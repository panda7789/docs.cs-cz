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
ms.openlocfilehash: 60c61e5b7c176f88e8f2c2e717e60ae40f43fbf6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255251"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="f56bd-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="f56bd-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="f56bd-103">Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.</span><span class="sxs-lookup"><span data-stu-id="f56bd-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
 <span data-ttu-id="f56bd-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f56bd-104">\<configuration></span></span>  
<span data-ttu-id="f56bd-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="f56bd-105">\<runtime></span></span>  
<span data-ttu-id="f56bd-106">\<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="f56bd-106">\<alwaysFlowImpersonationPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f56bd-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f56bd-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f56bd-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f56bd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f56bd-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f56bd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f56bd-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f56bd-110">Attributes</span></span>  
  
|<span data-ttu-id="f56bd-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f56bd-111">Attribute</span></span>|<span data-ttu-id="f56bd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f56bd-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f56bd-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="f56bd-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="f56bd-114">Určuje, zda Windows identity toky přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="f56bd-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f56bd-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="f56bd-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="f56bd-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f56bd-116">Value</span></span>|<span data-ttu-id="f56bd-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f56bd-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f56bd-118">Windows identity není téct přes asynchronní body, pokud se pomocí provádí zosobnění spravovaného metody, například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="f56bd-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="f56bd-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f56bd-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f56bd-120">Identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.</span><span class="sxs-lookup"><span data-stu-id="f56bd-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f56bd-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f56bd-121">Child Elements</span></span>  
 <span data-ttu-id="f56bd-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f56bd-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f56bd-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f56bd-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f56bd-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f56bd-124">Element</span></span>|<span data-ttu-id="f56bd-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f56bd-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f56bd-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f56bd-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f56bd-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="f56bd-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f56bd-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f56bd-128">Remarks</span></span>  
 <span data-ttu-id="f56bd-129">V rozhraní .NET Framework verze 1.0 a 1.1 identita Windows není téct přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="f56bd-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="f56bd-130">V rozhraní .NET Framework verze 2.0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěné vlákno a toky přes asynchronní body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="f56bd-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="f56bd-131"><xref:System.Security.Principal.WindowsIdentity> Také toků, která prochází přes asynchronní body, pokud zosobnění bylo dosaženo pomocí informací v rámci spravovaného metody, například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a ne prostřednictvím jiným způsobem, jako je například platforma vyvolání pro nativní metody.</span><span class="sxs-lookup"><span data-stu-id="f56bd-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="f56bd-132">Tento element slouží k určení, že identita Windows téct přes asynchronní body, bez ohledu na to, jak bylo dosaženo zosobnění.</span><span class="sxs-lookup"><span data-stu-id="f56bd-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="f56bd-133">Je-li změnit toto výchozí chování dvěma dalšími způsoby:</span><span class="sxs-lookup"><span data-stu-id="f56bd-133">You can alter this default behavior in two other ways:</span></span>  
  
1.  <span data-ttu-id="f56bd-134">Ve spravovaném kódu na základě vlákno.</span><span class="sxs-lookup"><span data-stu-id="f56bd-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="f56bd-135">Tok na základě vlákna můžete potlačit pomocí úpravy <xref:System.Threading.ExecutionContext> a <xref:System.Security.SecurityContext> nastavení pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f56bd-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="f56bd-136">Ve volání nespravovaných hostitelských rozhraní načíst modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="f56bd-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="f56bd-137">Pokud nespravovaných hostitelských rozhraní (místo jednoduchých spustitelný soubor spravovaný) slouží k načtení modulu CLR, můžete zadat speciální příznak ve volání [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="f56bd-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="f56bd-138">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) k `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span><span class="sxs-lookup"><span data-stu-id="f56bd-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f56bd-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="f56bd-139">Configuration File</span></span>  
 <span data-ttu-id="f56bd-140">V aplikaci .NET Framework Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f56bd-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="f56bd-141">Pro aplikace ASP.NET se dá nakonfigurovat tok zosobnění v soubor aspnet.config součástí \<složky Windows > \Microsoft.NET\Framework\vx.x.xxxx adresáře.</span><span class="sxs-lookup"><span data-stu-id="f56bd-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="f56bd-142">Technologie ASP.NET ve výchozím nastavení zakáže zosobnění tok v soubor aspnet.config pomocí následujících nastavení:</span><span class="sxs-lookup"><span data-stu-id="f56bd-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f56bd-143">V technologii ASP.NET Pokud chcete místo toho povolit tok zosobnění je nutné explicitně zadat následující nastavení:</span><span class="sxs-lookup"><span data-stu-id="f56bd-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="f56bd-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="f56bd-144">Example</span></span>  
 <span data-ttu-id="f56bd-145">Následující příklad ukazuje, jak určit, že identita Windows toky přes asynchronní body, i v případě, že zosobnění se dosahuje prostřednictvím znamená, že než spravovaných metod.</span><span class="sxs-lookup"><span data-stu-id="f56bd-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f56bd-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f56bd-146">See also</span></span>
- [<span data-ttu-id="f56bd-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="f56bd-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="f56bd-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="f56bd-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f56bd-149">\<legacyImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="f56bd-149">\<legacyImpersonationPolicy> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)
