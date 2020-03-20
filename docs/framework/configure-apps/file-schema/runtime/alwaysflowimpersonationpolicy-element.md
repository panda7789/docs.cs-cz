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
ms.openlocfilehash: 7c8ac37932a528ff0f000cbaab49124dec51b88c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154480"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="fde64-102">\<alwaysFlowImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="fde64-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="fde64-103">Určuje, že identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno.</span><span class="sxs-lookup"><span data-stu-id="fde64-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
<span data-ttu-id="fde64-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fde64-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fde64-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="fde64-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="fde64-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span><span class="sxs-lookup"><span data-stu-id="fde64-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**</span></span>\  
  
## <a name="syntax"></a><span data-ttu-id="fde64-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fde64-107">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fde64-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fde64-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fde64-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fde64-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fde64-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fde64-110">Attributes</span></span>  
  
|<span data-ttu-id="fde64-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fde64-111">Attribute</span></span>|<span data-ttu-id="fde64-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fde64-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fde64-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fde64-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fde64-114">Označuje, zda identita systému Windows proudí přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="fde64-114">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fde64-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="fde64-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fde64-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fde64-116">Value</span></span>|<span data-ttu-id="fde64-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fde64-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fde64-118">Identita systému Windows neprochází přes asynchronní body, pokud se zosobnění neprovádí pomocí spravovaných metod, jako je například <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span><span class="sxs-lookup"><span data-stu-id="fde64-118">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="fde64-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="fde64-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fde64-120">Identita systému Windows vždy proudí přes asynchronní body, bez ohledu na to, jak bylo zosobnění provedeno.</span><span class="sxs-lookup"><span data-stu-id="fde64-120">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fde64-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fde64-121">Child Elements</span></span>  
 <span data-ttu-id="fde64-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="fde64-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fde64-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fde64-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fde64-124">Element</span><span class="sxs-lookup"><span data-stu-id="fde64-124">Element</span></span>|<span data-ttu-id="fde64-125">Popis</span><span class="sxs-lookup"><span data-stu-id="fde64-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fde64-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fde64-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fde64-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fde64-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fde64-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fde64-128">Remarks</span></span>  
 <span data-ttu-id="fde64-129">V rozhraní .NET Framework verze 1.0 a 1.1 identita systému Windows neprobíhá přes asynchronní body.</span><span class="sxs-lookup"><span data-stu-id="fde64-129">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="fde64-130">V rozhraní .NET Framework verze 2.0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně spuštěné vlákno a toky přes asynchronní body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fde64-130">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="fde64-131">Také <xref:System.Security.Principal.WindowsIdentity> toky jako součást informací, které toky přes asynchronní body, za předpokladu, <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> že zosobnění bylo dosaženo pomocí spravovaných metod, jako jsou a nikoli prostřednictvím jiných prostředků, jako je například platforma vyvolat nativní metody.</span><span class="sxs-lookup"><span data-stu-id="fde64-131">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="fde64-132">Tento prvek se používá k určení, že identita systému Windows tok přes asynchronní body, bez ohledu na to, jak bylo dosaženo zosobnění.</span><span class="sxs-lookup"><span data-stu-id="fde64-132">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="fde64-133">Toto výchozí chování můžete změnit dvěma dalšími způsoby:</span><span class="sxs-lookup"><span data-stu-id="fde64-133">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="fde64-134">Ve spravovaném kódu pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="fde64-134">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="fde64-135">Tok můžete potlačit na základě vlákno úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> nastavení a <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>pomocí <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> nebo metoda.</span><span class="sxs-lookup"><span data-stu-id="fde64-135">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="fde64-136">Při volání nespravovaného hostitelského rozhraní načíst modul CLR (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="fde64-136">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="fde64-137">Pokud nespravované hostitelské rozhraní (namísto jednoduchého spravovaného spustitelného souboru) se používá k načtení CLR, můžete zadat speciální příznak ve volání [funkce CorBindToRuntimeEx.](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)</span><span class="sxs-lookup"><span data-stu-id="fde64-137">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="fde64-138">Chcete-li povolit režim kompatibility `flags` pro celý proces, nastavte parametr `STARTUP_ALWAYSFLOW_IMPERSONATION` [funkce CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na .</span><span class="sxs-lookup"><span data-stu-id="fde64-138">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fde64-139">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="fde64-139">Configuration File</span></span>  
 <span data-ttu-id="fde64-140">V aplikaci rozhraní .NET Framework lze tento prvek použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="fde64-140">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="fde64-141">Pro ASP.NET aplikaci lze tok zosobnění nakonfigurovat v souboru aspnet.config, který se nachází v \<adresáři Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="fde64-141">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="fde64-142">ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru aspnet.config pomocí následujících nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="fde64-142">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="fde64-143">V ASP.NET, pokud chcete povolit tok zosobnění místo, musíte explicitně použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="fde64-143">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="fde64-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="fde64-144">Example</span></span>  
 <span data-ttu-id="fde64-145">Následující příklad ukazuje, jak určit, že identita systému Windows toky přes asynchronní body, i v případě, že zosobnění je dosaženo prostřednictvím prostředků než spravované metody.</span><span class="sxs-lookup"><span data-stu-id="fde64-145">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fde64-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="fde64-146">See also</span></span>

- [<span data-ttu-id="fde64-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="fde64-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fde64-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fde64-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fde64-149">\<starší verze ImpersonationPolicy> Element</span><span class="sxs-lookup"><span data-stu-id="fde64-149">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
