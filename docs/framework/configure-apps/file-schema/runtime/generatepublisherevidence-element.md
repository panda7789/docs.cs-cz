---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645348"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="0ca55-102">\<generatePublisherEvidence> Element</span><span class="sxs-lookup"><span data-stu-id="0ca55-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="0ca55-103">Určuje, zda runtime <xref:System.Security.Policy.Publisher> vytvoří důkazy pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="0ca55-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="0ca55-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ca55-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0ca55-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0ca55-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="0ca55-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="0ca55-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca55-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ca55-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ca55-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ca55-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0ca55-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ca55-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ca55-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ca55-110">Attributes</span></span>  
  
|<span data-ttu-id="0ca55-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ca55-111">Attribute</span></span>|<span data-ttu-id="0ca55-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0ca55-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0ca55-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0ca55-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ca55-114">Určuje, zda soubor <xref:System.Security.Policy.Publisher> runtime vytvoří důkazy.</span><span class="sxs-lookup"><span data-stu-id="0ca55-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0ca55-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0ca55-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="0ca55-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0ca55-116">Value</span></span>|<span data-ttu-id="0ca55-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0ca55-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0ca55-118">Nevytváří <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="0ca55-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="0ca55-119">Vytváří <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="0ca55-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="0ca55-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="0ca55-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ca55-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0ca55-121">Child Elements</span></span>  
 <span data-ttu-id="0ca55-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="0ca55-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ca55-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0ca55-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0ca55-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ca55-124">Element</span></span>|<span data-ttu-id="0ca55-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0ca55-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0ca55-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ca55-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0ca55-127">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0ca55-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ca55-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ca55-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca55-129">V rozhraní .NET Framework 4 a novější tento prvek nemá žádný vliv na doby načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ca55-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="0ca55-130">Další informace naleznete v části Zjednodušení zásad zabezpečení v části [Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="0ca55-130">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="0ca55-131">Běžný jazyk runtime (CLR) se pokusí ověřit podpis Authenticode v době načítání k vytvoření <xref:System.Security.Policy.Publisher> legitimace pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ca55-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="0ca55-132">Ve výchozím nastavení však většina aplikací nepotřebujete <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="0ca55-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="0ca55-133">Standardní zásady CAS nezávisí na <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="0ca55-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="0ca55-134">Měli byste se vyhnout zbytečným nákladům na spuštění spojeným s ověřením podpisu vydavatele, pokud se <xref:System.Security.Permissions.PublisherIdentityPermission> aplikace nespustí v počítači s vlastními zásadami CAS nebo pokud nemá v úmyslu uspokojit požadavky v prostředí s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="0ca55-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="0ca55-135">(Požadavky na oprávnění identity vždy úspěšné v prostředí s plnou důvěryhodností.)</span><span class="sxs-lookup"><span data-stu-id="0ca55-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ca55-136">Doporučujeme, aby `<generatePublisherEvidence>` služby používat prvek ke zlepšení výkonu při spuštění.</span><span class="sxs-lookup"><span data-stu-id="0ca55-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="0ca55-137">Pomocí tohoto prvku můžete také pomoci vyhnout se zpoždění, které může způsobit časový odčasový čas a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="0ca55-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="0ca55-138">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="0ca55-138">Configuration File</span></span>  
 <span data-ttu-id="0ca55-139">Tento prvek lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="0ca55-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca55-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ca55-140">Example</span></span>  
 <span data-ttu-id="0ca55-141">Následující příklad ukazuje, jak `<generatePublisherEvidence>` pomocí prvku zakázat kontrolu zásad vydavatele CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0ca55-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ca55-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ca55-142">See also</span></span>

- [<span data-ttu-id="0ca55-143">Schéma nastavení běhu</span><span class="sxs-lookup"><span data-stu-id="0ca55-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0ca55-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0ca55-144">Configuration File Schema</span></span>](../index.md)
