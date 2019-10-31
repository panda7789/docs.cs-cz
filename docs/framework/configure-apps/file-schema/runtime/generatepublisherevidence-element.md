---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: b04ef53d6e9c3d954b0925ea8634b3d220b36af7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116575"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="7a8cb-102">\<element > generatePublisherEvidence</span><span class="sxs-lookup"><span data-stu-id="7a8cb-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="7a8cb-103">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimace pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="7a8cb-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="7a8cb-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7a8cb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7a8cb-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="7a8cb-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="7a8cb-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<generatePublisherEvidence >**</span><span class="sxs-lookup"><span data-stu-id="7a8cb-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a8cb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a8cb-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a8cb-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7a8cb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a8cb-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a8cb-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="7a8cb-110">Attributes</span></span>  
  
|<span data-ttu-id="7a8cb-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="7a8cb-111">Attribute</span></span>|<span data-ttu-id="7a8cb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7a8cb-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="7a8cb-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="7a8cb-114">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimace.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7a8cb-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="7a8cb-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="7a8cb-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7a8cb-116">Value</span></span>|<span data-ttu-id="7a8cb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="7a8cb-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="7a8cb-118">Nevytváří <xref:System.Security.Policy.Publisher> legitimace.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="7a8cb-119">Vytvoří legitimaci <xref:System.Security.Policy.Publisher>.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="7a8cb-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a8cb-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7a8cb-121">Child Elements</span></span>  
 <span data-ttu-id="7a8cb-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="7a8cb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a8cb-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7a8cb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7a8cb-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="7a8cb-124">Element</span></span>|<span data-ttu-id="7a8cb-125">Popis</span><span class="sxs-lookup"><span data-stu-id="7a8cb-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7a8cb-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7a8cb-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a8cb-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a8cb-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a8cb-129">V .NET Framework 4 a novějších, nemá tento prvek žádný vliv na časy načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="7a8cb-130">Další informace najdete v části "zjednodušení zásad zabezpečení" v článku [změny zabezpečení](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="7a8cb-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="7a8cb-131">Modul CLR (Common Language Runtime) se pokusí ověřit podpis Authenticode v době načítání a vytvořit <xref:System.Security.Policy.Publisher> legitimaci pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="7a8cb-132">Ve výchozím nastavení ale většina aplikací nepotřebuje <xref:System.Security.Policy.Publisher> legitimace.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="7a8cb-133">Standardní zásady CAS nespoléhají na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="7a8cb-134">Měli byste se vyhnout zbytečnému počátečnímu nákladům souvisejícím s ověřováním podpisu vydavatele, pokud se vaše aplikace nespustí na počítači s vlastními zásadami CAS, nebo má za následek splnění požadavků pro <xref:System.Security.Permissions.PublisherIdentityPermission> v prostředí s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="7a8cb-135">(Požadavky na oprávnění identity jsou vždycky úspěšné v prostředí s plnou důvěryhodností.)</span><span class="sxs-lookup"><span data-stu-id="7a8cb-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a8cb-136">Pro zlepšení výkonu při spuštění doporučujeme, aby služby používaly `<generatePublisherEvidence>` element.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="7a8cb-137">Použití tohoto prvku může také pomoci zabránit prodlevám, které mohou způsobit časový limit a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="7a8cb-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="7a8cb-138">Configuration File</span></span>  
 <span data-ttu-id="7a8cb-139">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a8cb-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a8cb-140">Example</span></span>  
 <span data-ttu-id="7a8cb-141">Následující příklad ukazuje, jak pomocí elementu `<generatePublisherEvidence>` zakázat kontrolu zásad vydavatele CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7a8cb-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a8cb-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a8cb-142">See also</span></span>

- [<span data-ttu-id="7a8cb-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="7a8cb-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7a8cb-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7a8cb-144">Configuration File Schema</span></span>](../index.md)
