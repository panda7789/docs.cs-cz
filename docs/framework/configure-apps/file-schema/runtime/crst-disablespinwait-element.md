---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f89f0558c11e229fef2ca3cd619e3c033f12c858
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754671"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="08349-102">\<Crst_DisableSpinWait > – element</span><span class="sxs-lookup"><span data-stu-id="08349-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="08349-103">Určuje, zda chcete zakázat typu číselník – časový limit na kritický oddíl, když ve sporných.</span><span class="sxs-lookup"><span data-stu-id="08349-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="08349-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="08349-104">\<configuration></span></span>  
<span data-ttu-id="08349-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="08349-105">\<runtime></span></span>  
<span data-ttu-id="08349-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="08349-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08349-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08349-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08349-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08349-108">Attributes and Elements</span></span>

<span data-ttu-id="08349-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08349-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08349-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="08349-110">Attributes</span></span>  
  
|<span data-ttu-id="08349-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="08349-111">Attribute</span></span>|<span data-ttu-id="08349-112">Popis</span><span class="sxs-lookup"><span data-stu-id="08349-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="08349-113">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="08349-113">**enabled**</span></span>|<span data-ttu-id="08349-114">Určuje, zda číselník – časový limit na kritické oddíly, když jsou jejich ve sporných zakázána.</span><span class="sxs-lookup"><span data-stu-id="08349-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="08349-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="08349-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="08349-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="08349-116">Value</span></span>|<span data-ttu-id="08349-117">Popis</span><span class="sxs-lookup"><span data-stu-id="08349-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="08349-118">1</span><span class="sxs-lookup"><span data-stu-id="08349-118">1</span></span>|<span data-ttu-id="08349-119">Zakážete typu číselník čekání, když kritický oddíl nelze získat.</span><span class="sxs-lookup"><span data-stu-id="08349-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="08349-120">0</span><span class="sxs-lookup"><span data-stu-id="08349-120">0</span></span>|<span data-ttu-id="08349-121">Nezakazujte čekání typu číselník při kritický oddíl nelze získat.</span><span class="sxs-lookup"><span data-stu-id="08349-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="08349-122">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="08349-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08349-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08349-123">Child Elements</span></span>  
 <span data-ttu-id="08349-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="08349-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08349-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08349-125">Parent Elements</span></span>  
  
|<span data-ttu-id="08349-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="08349-126">Element</span></span>|<span data-ttu-id="08349-127">Popis</span><span class="sxs-lookup"><span data-stu-id="08349-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="08349-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08349-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="08349-129">Obsahuje informace o různých nastavení konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="08349-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="08349-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="08349-130">Example</span></span>  

<span data-ttu-id="08349-131">Následující příklad zakazuje typu číselník čekání v kritických oddílů, když ve sporných.</span><span class="sxs-lookup"><span data-stu-id="08349-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08349-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08349-132">See also</span></span>

- [<span data-ttu-id="08349-133">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="08349-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="08349-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="08349-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
