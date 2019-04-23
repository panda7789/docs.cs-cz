---
title: element < Crst_DisableSpinWait >
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cde26250db0b3d11c51a18b7ebd378953ae0958
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982175"
---
# <a name="crstdisablespinwait-element"></a><span data-ttu-id="e097e-102">\<Crst_DisableSpinWait > – element</span><span class="sxs-lookup"><span data-stu-id="e097e-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="e097e-103">Určuje, zda chcete zakázat typu číselník – časový limit na kritický oddíl, když ve sporných.</span><span class="sxs-lookup"><span data-stu-id="e097e-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span> \ 
  
 <span data-ttu-id="e097e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e097e-104">\<configuration></span></span>  
<span data-ttu-id="e097e-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="e097e-105">\<runtime></span></span>  
<span data-ttu-id="e097e-106">\<Crst_DisableSpinWait></span><span class="sxs-lookup"><span data-stu-id="e097e-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e097e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e097e-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e097e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e097e-108">Attributes and Elements</span></span>

<span data-ttu-id="e097e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e097e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e097e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e097e-110">Attributes</span></span>  
  
|<span data-ttu-id="e097e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e097e-111">Attribute</span></span>|<span data-ttu-id="e097e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e097e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e097e-113">**Povoleno**</span><span class="sxs-lookup"><span data-stu-id="e097e-113">**enabled**</span></span>|<span data-ttu-id="e097e-114">Určuje, zda je povoleno typu číselník – časový limit na kritické oddíly, když jsou jejich ve sporných.</span><span class="sxs-lookup"><span data-stu-id="e097e-114">Specifies whether spin-waiting for critical sections is enabled when they are contended.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="e097e-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="e097e-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="e097e-116">Value</span><span class="sxs-lookup"><span data-stu-id="e097e-116">Value</span></span>|<span data-ttu-id="e097e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e097e-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e097e-118">1</span><span class="sxs-lookup"><span data-stu-id="e097e-118">1</span></span>|<span data-ttu-id="e097e-119">Otočit waiting je povolená.</span><span class="sxs-lookup"><span data-stu-id="e097e-119">Spin-waiting is enabled.</span></span>|  
|<span data-ttu-id="e097e-120">0</span><span class="sxs-lookup"><span data-stu-id="e097e-120">0</span></span>|<span data-ttu-id="e097e-121">Otočit waiting je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="e097e-121">Spin-waiting is disabled.</span></span> <span data-ttu-id="e097e-122">Toto je výchozí</span><span class="sxs-lookup"><span data-stu-id="e097e-122">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e097e-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e097e-123">Child Elements</span></span>  
 <span data-ttu-id="e097e-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e097e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e097e-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e097e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e097e-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="e097e-126">Element</span></span>|<span data-ttu-id="e097e-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e097e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e097e-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e097e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e097e-129">Obsahuje informace o různých nastavení konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e097e-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e097e-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="e097e-130">Example</span></span>  

<span data-ttu-id="e097e-131">Následující příklad zakazuje typu číselník čekání v kritických oddílů, když ve sporných.</span><span class="sxs-lookup"><span data-stu-id="e097e-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e097e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e097e-132">See also</span></span>

- [<span data-ttu-id="e097e-133">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="e097e-133">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="e097e-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e097e-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
