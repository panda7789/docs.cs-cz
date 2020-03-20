---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 24a5ea02992a5bce681b5bab4fb7f75505bd225d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154111"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="ec9ea-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="ec9ea-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="ec9ea-103">Určuje, zda runtime <xref:System.Security.Policy.Publisher> vytvoří důkazy pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="ec9ea-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="ec9ea-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec9ea-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ec9ea-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec9ea-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ec9ea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="ec9ea-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec9ea-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec9ea-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec9ea-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ec9ea-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ec9ea-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec9ea-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ec9ea-110">Attributes</span></span>  
  
|<span data-ttu-id="ec9ea-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ec9ea-111">Attribute</span></span>|<span data-ttu-id="ec9ea-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ec9ea-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ec9ea-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ec9ea-114">Určuje, zda soubor <xref:System.Security.Policy.Publisher> runtime vytvoří důkazy.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ec9ea-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ec9ea-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ec9ea-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ec9ea-116">Value</span></span>|<span data-ttu-id="ec9ea-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ec9ea-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ec9ea-118">Nevytváří <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="ec9ea-119">Vytváří <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ec9ea-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec9ea-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ec9ea-121">Child Elements</span></span>  
 <span data-ttu-id="ec9ea-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec9ea-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ec9ea-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ec9ea-124">Element</span><span class="sxs-lookup"><span data-stu-id="ec9ea-124">Element</span></span>|<span data-ttu-id="ec9ea-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ec9ea-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ec9ea-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ec9ea-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec9ea-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ec9ea-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec9ea-129">V rozhraní .NET Framework 4 a novější tento prvek nemá žádný vliv na doby načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="ec9ea-130">Další informace naleznete v části Zjednodušení zásad zabezpečení v části [Změny zabezpečení](../../../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ec9ea-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="ec9ea-131">Běžný jazyk runtime (CLR) se pokusí ověřit podpis Authenticode v době načítání k vytvoření <xref:System.Security.Policy.Publisher> legitimace pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="ec9ea-132">Ve výchozím nastavení však většina aplikací nepotřebujete <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="ec9ea-133">Standardní zásady CAS nezávisí na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="ec9ea-134">Měli byste se vyhnout zbytečným nákladům na spuštění spojeným s ověřením podpisu vydavatele, pokud se <xref:System.Security.Permissions.PublisherIdentityPermission> aplikace nespustí v počítači s vlastními zásadami CAS nebo pokud nemá v úmyslu uspokojit požadavky v prostředí s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="ec9ea-135">(Požadavky na oprávnění identity vždy úspěšné v prostředí s plnou důvěryhodností.)</span><span class="sxs-lookup"><span data-stu-id="ec9ea-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec9ea-136">Doporučujeme, aby `<generatePublisherEvidence>` služby používat prvek ke zlepšení výkonu při spuštění.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="ec9ea-137">Pomocí tohoto prvku můžete také pomoci vyhnout se zpoždění, které může způsobit časový odčasový čas a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="ec9ea-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="ec9ea-138">Configuration File</span></span>  
 <span data-ttu-id="ec9ea-139">Tento prvek lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec9ea-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec9ea-140">Example</span></span>  
 <span data-ttu-id="ec9ea-141">Následující příklad ukazuje, jak `<generatePublisherEvidence>` pomocí prvku zakázat kontrolu zásad vydavatele CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec9ea-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec9ea-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="ec9ea-142">See also</span></span>

- [<span data-ttu-id="ec9ea-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ec9ea-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ec9ea-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ec9ea-144">Configuration File Schema</span></span>](../index.md)
