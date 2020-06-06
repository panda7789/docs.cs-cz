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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154480"
---
# <a name="alwaysflowimpersonationpolicy-element"></a><span data-ttu-id="a63f3-102">Element \<alwaysFlowImpersonationPolicy></span><span class="sxs-lookup"><span data-stu-id="a63f3-102">\<alwaysFlowImpersonationPolicy> Element</span></span>
<span data-ttu-id="a63f3-103">Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="a63f3-103">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<alwaysFlowImpersonationPolicy>**\  
  
## <a name="syntax"></a><span data-ttu-id="a63f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a63f3-104">Syntax</span></span>  
  
```xml  
<alwaysFlowImpersonationPolicy
  enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a63f3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a63f3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a63f3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a63f3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a63f3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a63f3-107">Attributes</span></span>  
  
|<span data-ttu-id="a63f3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a63f3-108">Attribute</span></span>|<span data-ttu-id="a63f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a63f3-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a63f3-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a63f3-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a63f3-111">Určuje, zda se v rámci asynchronních bodů využívá identita systému Windows.</span><span class="sxs-lookup"><span data-stu-id="a63f3-111">Indicates whether the Windows identity flows across asynchronous points.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a63f3-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a63f3-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="a63f3-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a63f3-113">Value</span></span>|<span data-ttu-id="a63f3-114">Description</span><span class="sxs-lookup"><span data-stu-id="a63f3-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a63f3-115">Identita systému Windows není předávána mezi asynchronními body, pokud zosobnění není provedeno prostřednictvím spravovaných metod, jako je <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> .</span><span class="sxs-lookup"><span data-stu-id="a63f3-115">The Windows identity does not flow across asynchronous points, unless the impersonation is performed through managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A>.</span></span> <span data-ttu-id="a63f3-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a63f3-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a63f3-117">Identita systému Windows vždy přetéká napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="a63f3-117">The Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a63f3-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a63f3-118">Child Elements</span></span>  
 <span data-ttu-id="a63f3-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="a63f3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a63f3-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a63f3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a63f3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a63f3-121">Element</span></span>|<span data-ttu-id="a63f3-122">Description</span><span class="sxs-lookup"><span data-stu-id="a63f3-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a63f3-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a63f3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a63f3-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="a63f3-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a63f3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a63f3-125">Remarks</span></span>  
 <span data-ttu-id="a63f3-126">V .NET Framework verzích 1,0 a 1,1 neprovádí identita systému Windows tok mezi asynchronními body.</span><span class="sxs-lookup"><span data-stu-id="a63f3-126">In the .NET Framework versions 1.0 and 1.1, the Windows identity does not flow across asynchronous points.</span></span> <span data-ttu-id="a63f3-127">V .NET Framework verze 2,0 je <xref:System.Threading.ExecutionContext> objekt, který obsahuje informace o aktuálně vykonávajícím vlákně a přenáší je napříč asynchronními body v rámci domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a63f3-127">In the .NET Framework version 2.0, there is an <xref:System.Threading.ExecutionContext> object that contains information about the currently executing thread, and flows it across asynchronous points within an application domain.</span></span> <span data-ttu-id="a63f3-128">Také se přenáší <xref:System.Security.Principal.WindowsIdentity> jako součást informací, které jsou v průběhu asynchronních bodů za předpokladu, že došlo k zosobnění pomocí spravovaných metod, jako je <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> a nikoli prostřednictvím jiných prostředků, jako je vyvolání platformy pro nativní metody.</span><span class="sxs-lookup"><span data-stu-id="a63f3-128">The <xref:System.Security.Principal.WindowsIdentity> also flows as part of the information that flows across the asynchronous points, provided the impersonation was achieved using managed methods such as <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> and not through other means such as platform invoke to native methods.</span></span> <span data-ttu-id="a63f3-129">Tento prvek slouží k určení toho, že identita systému Windows probíhá přes asynchronní body bez ohledu na to, jakým způsobem bylo dosaženo zosobnění.</span><span class="sxs-lookup"><span data-stu-id="a63f3-129">This element is used to specify that the Windows identity does flow across asynchronous points, regardless of how the impersonation was achieved.</span></span>  
  
 <span data-ttu-id="a63f3-130">Výchozí chování můžete změnit dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="a63f3-130">You can alter this default behavior in two other ways:</span></span>  
  
1. <span data-ttu-id="a63f3-131">Ve spravovaném kódu v závislosti na vlákně.</span><span class="sxs-lookup"><span data-stu-id="a63f3-131">In managed code on a per-thread basis.</span></span>  
  
     <span data-ttu-id="a63f3-132">Tok můžete potlačit na základě jednotlivých vláken úpravou <xref:System.Threading.ExecutionContext> <xref:System.Security.SecurityContext> nastavení a pomocí <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType> <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType> metody, nebo <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a63f3-132">You can suppress the flow on a per-thread basis by modifying the <xref:System.Threading.ExecutionContext> and <xref:System.Security.SecurityContext> settings by using the <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=nameWithType>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=nameWithType>, or <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="a63f3-133">Ve volání nespravovaného hostitelského rozhraní pro načtení modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a63f3-133">In the call to the unmanaged hosting interface to load the common language runtime (CLR).</span></span>  
  
     <span data-ttu-id="a63f3-134">Pokud se pro načtení CLR používá nespravované rozhraní hostování (namísto jednoduchého spravovaného spustitelného souboru), můžete zadat speciální příznak ve volání funkce [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) .</span><span class="sxs-lookup"><span data-stu-id="a63f3-134">If an unmanaged hosting interface (instead of a simple managed executable) is used to load the CLR, you can specify a special flag in the call to the [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) function.</span></span> <span data-ttu-id="a63f3-135">Chcete-li povolit režim kompatibility pro celý proces, nastavte `flags` parametr pro [funkci CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) na `STARTUP_ALWAYSFLOW_IMPERSONATION` .</span><span class="sxs-lookup"><span data-stu-id="a63f3-135">To enable the compatibility mode for the entire process, set the `flags` parameter for [CorBindToRuntimeEx Function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) to `STARTUP_ALWAYSFLOW_IMPERSONATION`.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a63f3-136">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a63f3-136">Configuration File</span></span>  
 <span data-ttu-id="a63f3-137">V .NET Framework aplikaci lze tento prvek použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a63f3-137">In a .NET Framework application, this element can be used only in the application configuration file.</span></span>  
  
 <span data-ttu-id="a63f3-138">V případě aplikace ASP.NET může být tok zosobnění konfigurován v souboru ASPNET. config, který najdete v \<Windows Folder> adresáři \Microsoft.NET\Framework\vx.x.xxxx.</span><span class="sxs-lookup"><span data-stu-id="a63f3-138">For an ASP.NET application, the impersonation flow can be configured in the aspnet.config file found in the \<Windows Folder>\Microsoft.NET\Framework\vx.x.xxxx directory.</span></span>  
  
 <span data-ttu-id="a63f3-139">ASP.NET ve výchozím nastavení zakáže tok zosobnění v souboru ASPNET. config pomocí následujících nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a63f3-139">ASP.NET by default disables the impersonation flow in the aspnet.config file by using the following configuration settings:</span></span>  
  
```xml
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a63f3-140">Pokud chcete místo toho použít tok zosobnění, musíte v ASP.NET explicitně použít následující nastavení konfigurace:</span><span class="sxs-lookup"><span data-stu-id="a63f3-140">In ASP.NET, if you want to allow the flow of impersonation instead, you must explicitly use the following configuration settings:</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="example"></a><span data-ttu-id="a63f3-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="a63f3-141">Example</span></span>  
 <span data-ttu-id="a63f3-142">Následující příklad ukazuje, jak určit, že se má identita systému Windows provádět napříč asynchronními body, a to i v případě, že je možné zosobnění dosáhnout prostřednictvím jiných prostředků než spravovaných metod.</span><span class="sxs-lookup"><span data-stu-id="a63f3-142">The following example shows how to specify that the Windows identity flows across asynchronous points, even when the impersonation is achieved through means other than managed methods.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a63f3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="a63f3-143">See also</span></span>

- [<span data-ttu-id="a63f3-144">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a63f3-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a63f3-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a63f3-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a63f3-146">\<legacyImpersonationPolicy>Objekt</span><span class="sxs-lookup"><span data-stu-id="a63f3-146">\<legacyImpersonationPolicy> Element</span></span>](legacyimpersonationpolicy-element.md)
