---
title: Element <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0253c3ced52b575097fe5d18abb8ce188c0164fb
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252687"
---
# <a name="developmentmode-element"></a><span data-ttu-id="76272-102">\<developmentMode – element ></span><span class="sxs-lookup"><span data-stu-id="76272-102">\<developmentMode> Element</span></span>
<span data-ttu-id="76272-103">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
<span data-ttu-id="76272-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="76272-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="76272-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="76272-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="76272-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<developmentMode>**</span><span class="sxs-lookup"><span data-stu-id="76272-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76272-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76272-107">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76272-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76272-108">Attributes and Elements</span></span>  
 <span data-ttu-id="76272-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76272-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76272-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="76272-110">Attributes</span></span>  
  
|<span data-ttu-id="76272-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="76272-111">Attribute</span></span>|<span data-ttu-id="76272-112">Popis</span><span class="sxs-lookup"><span data-stu-id="76272-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76272-113">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="76272-113">**developerInstallation**</span></span>|<span data-ttu-id="76272-114">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-114">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="76272-115">developerInstallation – atribut</span><span class="sxs-lookup"><span data-stu-id="76272-115">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="76272-116">Value</span><span class="sxs-lookup"><span data-stu-id="76272-116">Value</span></span>|<span data-ttu-id="76272-117">Popis</span><span class="sxs-lookup"><span data-stu-id="76272-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76272-118">**true**</span><span class="sxs-lookup"><span data-stu-id="76272-118">**true**</span></span>|<span data-ttu-id="76272-119">Vyhledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-119">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="76272-120">**false**</span><span class="sxs-lookup"><span data-stu-id="76272-120">**false**</span></span>|<span data-ttu-id="76272-121">Nehledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-121">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="76272-122">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="76272-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76272-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76272-123">Child Elements</span></span>  
 <span data-ttu-id="76272-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="76272-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76272-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76272-125">Parent Elements</span></span>  
  
|<span data-ttu-id="76272-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="76272-126">Element</span></span>|<span data-ttu-id="76272-127">Popis</span><span class="sxs-lookup"><span data-stu-id="76272-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="76272-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="76272-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="76272-129">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="76272-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76272-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76272-130">Remarks</span></span>  
 <span data-ttu-id="76272-131">Toto nastavení použijte pouze v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="76272-131">Use this setting only at development time.</span></span> <span data-ttu-id="76272-132">Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-132">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="76272-133">Jednoduše používá první nalezené sestavení.</span><span class="sxs-lookup"><span data-stu-id="76272-133">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76272-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="76272-134">Example</span></span>  
 <span data-ttu-id="76272-135">Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="76272-135">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="76272-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76272-136">See also</span></span>

- [<span data-ttu-id="76272-137">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="76272-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="76272-138">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="76272-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="76272-139">Postupy: Hledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="76272-139">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
