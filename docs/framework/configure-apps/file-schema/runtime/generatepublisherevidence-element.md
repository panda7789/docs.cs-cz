---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0861436ca727d63cdae58e3222826bf6414610
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489452"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="ebd8e-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="ebd8e-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="ebd8e-103">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkazy pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="ebd8e-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="ebd8e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ebd8e-104">\<configuration></span></span>  
<span data-ttu-id="ebd8e-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="ebd8e-105">\<runtime></span></span>  
<span data-ttu-id="ebd8e-106">\<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="ebd8e-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd8e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebd8e-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebd8e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ebd8e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ebd8e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebd8e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ebd8e-110">Attributes</span></span>  
  
|<span data-ttu-id="ebd8e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ebd8e-111">Attribute</span></span>|<span data-ttu-id="ebd8e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ebd8e-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ebd8e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ebd8e-114">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ebd8e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ebd8e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ebd8e-116">Value</span><span class="sxs-lookup"><span data-stu-id="ebd8e-116">Value</span></span>|<span data-ttu-id="ebd8e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ebd8e-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ebd8e-118">Nevytváří žádné <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="ebd8e-119">Vytvoří <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ebd8e-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ebd8e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ebd8e-121">Child Elements</span></span>  
 <span data-ttu-id="ebd8e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="ebd8e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ebd8e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ebd8e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ebd8e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ebd8e-124">Element</span></span>|<span data-ttu-id="ebd8e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ebd8e-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ebd8e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ebd8e-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebd8e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ebd8e-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebd8e-129">V rozhraní .NET Framework 4 nebo novější Tento element nemá žádný vliv na dobu načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="ebd8e-130">Další informace najdete v části "Zjednodušení zásady zabezpečení" v [změny zabezpečení](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ebd8e-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="ebd8e-131">Modul CLR (CLR) pokusí o ověření podpisu Authenticode v okamžiku načtení vytvořit <xref:System.Security.Policy.Publisher> legitimaci sestavení.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="ebd8e-132">Ale ve výchozím nastavení, většina aplikací není nutné <xref:System.Security.Policy.Publisher> důkaz.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ebd8e-133">Standardní zásady CAS nespoléhá na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="ebd8e-134">Měli byste se vyhnout zbytečným spuštění náklady spojené s ověření podpisu vydavatele, pokud vaše aplikace spustí na počítači s vlastní zásady CAS nebo hodlá splňovat požadavky pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="ebd8e-135">(Požadavky na identity oprávnění vždy úspěšné v prostředí úplného vztahu důvěryhodnosti.)</span><span class="sxs-lookup"><span data-stu-id="ebd8e-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebd8e-136">Doporučujeme vám, které služby použijte `<generatePublisherEvidence>` elementu, chcete-li zlepšit výkon při spuštění.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="ebd8e-137">Použití tohoto prvku může také pomoct vyhnout se prodlevám, které může způsobit vypršení časového limitu a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ebd8e-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ebd8e-138">Configuration File</span></span>  
 <span data-ttu-id="ebd8e-139">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebd8e-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebd8e-140">Example</span></span>  
 <span data-ttu-id="ebd8e-141">Následující příklad ukazuje způsob použití `<generatePublisherEvidence>` prvek, který chcete zakázat kontrolu pro certifikační Autority zásad vydavatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="ebd8e-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebd8e-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebd8e-142">See also</span></span>

- [<span data-ttu-id="ebd8e-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ebd8e-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ebd8e-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ebd8e-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
