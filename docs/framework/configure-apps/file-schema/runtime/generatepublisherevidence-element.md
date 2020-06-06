---
title: Element <generatePublisherEvidence>
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "81645348"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="a846c-102">Element \<generatePublisherEvidence></span><span class="sxs-lookup"><span data-stu-id="a846c-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="a846c-103">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimaci pro zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="a846c-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="a846c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a846c-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a846c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a846c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a846c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a846c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a846c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="a846c-107">Attributes</span></span>  
  
|<span data-ttu-id="a846c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="a846c-108">Attribute</span></span>|<span data-ttu-id="a846c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a846c-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a846c-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="a846c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="a846c-111">Určuje, zda modul runtime vytvoří <xref:System.Security.Policy.Publisher> legitimaci.</span><span class="sxs-lookup"><span data-stu-id="a846c-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a846c-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="a846c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="a846c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a846c-113">Value</span></span>|<span data-ttu-id="a846c-114">Description</span><span class="sxs-lookup"><span data-stu-id="a846c-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a846c-115">Nevytváří <xref:System.Security.Policy.Publisher> legitimace.</span><span class="sxs-lookup"><span data-stu-id="a846c-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="a846c-116">Vytvoří <xref:System.Security.Policy.Publisher> legitimaci.</span><span class="sxs-lookup"><span data-stu-id="a846c-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="a846c-117">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a846c-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a846c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a846c-118">Child Elements</span></span>  
 <span data-ttu-id="a846c-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="a846c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a846c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a846c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a846c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="a846c-121">Element</span></span>|<span data-ttu-id="a846c-122">Description</span><span class="sxs-lookup"><span data-stu-id="a846c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a846c-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a846c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a846c-124">Obsahuje informace o možnostech inicializace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="a846c-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a846c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a846c-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a846c-126">V .NET Framework 4 a novějších, nemá tento prvek žádný vliv na časy načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="a846c-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="a846c-127">Další informace najdete v části "zjednodušení zásad zabezpečení" v článku [změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="a846c-127">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="a846c-128">Modul CLR (Common Language Runtime) se pokusí ověřit podpis Authenticode v době načítání a vytvořit <xref:System.Security.Policy.Publisher> legitimaci pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="a846c-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="a846c-129">Ve výchozím nastavení ale většina aplikací nepotřebuje <xref:System.Security.Policy.Publisher> důkazy.</span><span class="sxs-lookup"><span data-stu-id="a846c-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="a846c-130">Standardní zásady CAS nezávisí na <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="a846c-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="a846c-131">Měli byste se vyhnout zbytečnému počátečnímu nákladům souvisejícím s ověřováním podpisu vydavatele, pokud vaše aplikace neběží na počítači s vlastními zásadami CAS, nebo má v úmyslu splňovat požadavky pro <xref:System.Security.Permissions.PublisherIdentityPermission> prostředí s částečnou důvěryhodností.</span><span class="sxs-lookup"><span data-stu-id="a846c-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="a846c-132">(Požadavky na oprávnění identity jsou vždycky úspěšné v prostředí s plnou důvěryhodností.)</span><span class="sxs-lookup"><span data-stu-id="a846c-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a846c-133">Pro zlepšení výkonu při spouštění doporučujeme, aby služby používaly tento `<generatePublisherEvidence>` prvek.</span><span class="sxs-lookup"><span data-stu-id="a846c-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="a846c-134">Použití tohoto prvku může také pomoci zabránit prodlevám, které mohou způsobit časový limit a zrušení spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a846c-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a846c-135">Konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="a846c-135">Configuration File</span></span>  
 <span data-ttu-id="a846c-136">Tento element lze použít pouze v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="a846c-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a846c-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="a846c-137">Example</span></span>  
 <span data-ttu-id="a846c-138">Následující příklad ukazuje, jak použít `<generatePublisherEvidence>` element k zakázání kontroly zásad vydavatele CAS pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a846c-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a846c-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="a846c-139">See also</span></span>

- [<span data-ttu-id="a846c-140">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a846c-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a846c-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="a846c-141">Configuration File Schema</span></span>](../index.md)
