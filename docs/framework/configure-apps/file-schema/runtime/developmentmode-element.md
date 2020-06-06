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
ms.openlocfilehash: 4a062da31740edb8f0c7a4f4db8b09800c687587
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117622"
---
# <a name="developmentmode-element"></a><span data-ttu-id="8ea82-102">Element \<developmentMode></span><span class="sxs-lookup"><span data-stu-id="8ea82-102">\<developmentMode> Element</span></span>
<span data-ttu-id="8ea82-103">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-103">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="8ea82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ea82-104">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ea82-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8ea82-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8ea82-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8ea82-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ea82-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8ea82-107">Attributes</span></span>  
  
|<span data-ttu-id="8ea82-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8ea82-108">Attribute</span></span>|<span data-ttu-id="8ea82-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8ea82-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ea82-110">**developerInstallation**</span><span class="sxs-lookup"><span data-stu-id="8ea82-110">**developerInstallation**</span></span>|<span data-ttu-id="8ea82-111">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-111">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="8ea82-112">developerInstallation – atribut</span><span class="sxs-lookup"><span data-stu-id="8ea82-112">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="8ea82-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8ea82-113">Value</span></span>|<span data-ttu-id="8ea82-114">Description</span><span class="sxs-lookup"><span data-stu-id="8ea82-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8ea82-115">**podmínka**</span><span class="sxs-lookup"><span data-stu-id="8ea82-115">**true**</span></span>|<span data-ttu-id="8ea82-116">Vyhledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-116">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="8ea82-117">**chybné**</span><span class="sxs-lookup"><span data-stu-id="8ea82-117">**false**</span></span>|<span data-ttu-id="8ea82-118">Nehledá sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-118">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="8ea82-119">Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="8ea82-119">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ea82-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8ea82-120">Child Elements</span></span>  
 <span data-ttu-id="8ea82-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="8ea82-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ea82-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8ea82-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8ea82-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="8ea82-123">Element</span></span>|<span data-ttu-id="8ea82-124">Description</span><span class="sxs-lookup"><span data-stu-id="8ea82-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8ea82-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ea82-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8ea82-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8ea82-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ea82-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ea82-127">Remarks</span></span>  
 <span data-ttu-id="8ea82-128">Toto nastavení použijte pouze v době vývoje.</span><span class="sxs-lookup"><span data-stu-id="8ea82-128">Use this setting only at development time.</span></span> <span data-ttu-id="8ea82-129">Modul runtime nekontroluje verze v sestaveních se silným názvem nalezenými v mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-129">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="8ea82-130">Jednoduše používá první nalezené sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ea82-130">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ea82-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="8ea82-131">Example</span></span>  
 <span data-ttu-id="8ea82-132">Následující příklad ukazuje, jak způsobit, aby modul runtime vyhledal sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="8ea82-132">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ea82-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ea82-133">See also</span></span>

- [<span data-ttu-id="8ea82-134">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="8ea82-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8ea82-135">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8ea82-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="8ea82-136">Postupy: Vyhledání sestavení pomocí mechanismu DEVPATH</span><span class="sxs-lookup"><span data-stu-id="8ea82-136">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
