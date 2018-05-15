---
title: '&lt;generatePublisherEvidence&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="adeb7-102">&lt;generatePublisherEvidence&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="adeb7-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="adeb7-103">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkaz pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="adeb7-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="adeb7-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="adeb7-104">\<configuration></span></span>  
<span data-ttu-id="adeb7-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="adeb7-105">\<runtime></span></span>  
<span data-ttu-id="adeb7-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="adeb7-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adeb7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adeb7-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adeb7-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="adeb7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="adeb7-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="adeb7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adeb7-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="adeb7-110">Attributes</span></span>  
  
|<span data-ttu-id="adeb7-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="adeb7-111">Attribute</span></span>|<span data-ttu-id="adeb7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="adeb7-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="adeb7-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="adeb7-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="adeb7-114">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="adeb7-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="adeb7-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="adeb7-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="adeb7-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="adeb7-116">Value</span></span>|<span data-ttu-id="adeb7-117">Popis</span><span class="sxs-lookup"><span data-stu-id="adeb7-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="adeb7-118">Nevytváří <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="adeb7-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="adeb7-119">Vytvoří <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="adeb7-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="adeb7-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="adeb7-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adeb7-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="adeb7-121">Child Elements</span></span>  
 <span data-ttu-id="adeb7-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="adeb7-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adeb7-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="adeb7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="adeb7-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="adeb7-124">Element</span></span>|<span data-ttu-id="adeb7-125">Popis</span><span class="sxs-lookup"><span data-stu-id="adeb7-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="adeb7-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adeb7-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="adeb7-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="adeb7-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adeb7-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adeb7-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adeb7-129">V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] a později tento element nemá žádný vliv na časů načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="adeb7-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="adeb7-130">Další informace najdete v části "Zjednodušení zásad zabezpečení" v [změny zabezpečení](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="adeb7-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="adeb7-131">Modul CLR (CLR) pokusí se ověřit podpis Authenticode při načítání, chcete-li vytvořit <xref:System.Security.Policy.Publisher> důkaz pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="adeb7-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="adeb7-132">Nicméně ve výchozím nastavení, většina aplikací není nutné <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="adeb7-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="adeb7-133">Standardní zásady certifikační Autority na nespoléhá se <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="adeb7-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="adeb7-134">Neměli byste nepotřebné spuštění náklady spojené s ověření podpisu vydavatele, pokud vaše aplikace spustí na počítači s vlastní zásadu CAS nebo je hodláte splňují požadavky pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="adeb7-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="adeb7-135">(Požadavky pro oprávnění identity vždy úspěšné v prostředí plné důvěryhodnosti.)</span><span class="sxs-lookup"><span data-stu-id="adeb7-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adeb7-136">Doporučujeme, který služeb pomocí `<generatePublisherEvidence>` elementu, který chcete zvýšit výkon při spouštění.</span><span class="sxs-lookup"><span data-stu-id="adeb7-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="adeb7-137">Pomocí tohoto elementu může také pomoci zabránit zpoždění, které může způsobit, že vypršení časového limitu a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="adeb7-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="adeb7-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="adeb7-138">Configuration File</span></span>  
 <span data-ttu-id="adeb7-139">Tento element může použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="adeb7-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adeb7-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="adeb7-140">Example</span></span>  
 <span data-ttu-id="adeb7-141">Následující příklad ukazuje způsob použití `<generatePublisherEvidence>` elementu, který chcete zakázat zjišťování certifikační Autority zásad vydavatele pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="adeb7-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adeb7-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="adeb7-142">See Also</span></span>  
 [<span data-ttu-id="adeb7-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="adeb7-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="adeb7-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="adeb7-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
