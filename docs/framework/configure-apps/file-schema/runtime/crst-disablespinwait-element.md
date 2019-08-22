---
title: < element > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a52dd671f1fbf6fda5bdc92c0935784181eb4b03
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663844"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="27c0d-102">\<Crst_DisableSpinWait – element ></span><span class="sxs-lookup"><span data-stu-id="27c0d-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="27c0d-103">Určuje, jestli se má v případě, že se má v případě, že je to zamýšlí, zakázat číselník čekání</span><span class="sxs-lookup"><span data-stu-id="27c0d-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
 <span data-ttu-id="27c0d-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="27c0d-104">\<configuration></span></span>  
<span data-ttu-id="27c0d-105">\<> modulu runtime</span><span class="sxs-lookup"><span data-stu-id="27c0d-105">\<runtime></span></span>  
<span data-ttu-id="27c0d-106">\<Crst_DisableSpinWait ></span><span class="sxs-lookup"><span data-stu-id="27c0d-106">\<Crst_DisableSpinWait></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27c0d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27c0d-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27c0d-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="27c0d-108">Attributes and Elements</span></span>

<span data-ttu-id="27c0d-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="27c0d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27c0d-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="27c0d-110">Attributes</span></span>  
  
|<span data-ttu-id="27c0d-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="27c0d-111">Attribute</span></span>|<span data-ttu-id="27c0d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="27c0d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="27c0d-113">**umožněn**</span><span class="sxs-lookup"><span data-stu-id="27c0d-113">**enabled**</span></span>|<span data-ttu-id="27c0d-114">Určuje, jestli jsou zakázané oddíly, které čekají na kritické, pokud jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="27c0d-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="27c0d-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="27c0d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="27c0d-116">Value</span><span class="sxs-lookup"><span data-stu-id="27c0d-116">Value</span></span>|<span data-ttu-id="27c0d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="27c0d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="27c0d-118">1</span><span class="sxs-lookup"><span data-stu-id="27c0d-118">1</span></span>|<span data-ttu-id="27c0d-119">Zakažte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="27c0d-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="27c0d-120">0</span><span class="sxs-lookup"><span data-stu-id="27c0d-120">0</span></span>|<span data-ttu-id="27c0d-121">Nepovolujte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="27c0d-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="27c0d-122">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="27c0d-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="27c0d-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="27c0d-123">Child Elements</span></span>  
 <span data-ttu-id="27c0d-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="27c0d-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="27c0d-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="27c0d-125">Parent Elements</span></span>  
  
|<span data-ttu-id="27c0d-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="27c0d-126">Element</span></span>|<span data-ttu-id="27c0d-127">Popis</span><span class="sxs-lookup"><span data-stu-id="27c0d-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="27c0d-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27c0d-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="27c0d-129">Obsahuje informace o různých nastaveních konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="27c0d-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="27c0d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="27c0d-130">Example</span></span>  

<span data-ttu-id="27c0d-131">Následující příklad v případě, že je to zamýšlí, zakáže v částech kritické čekání.</span><span class="sxs-lookup"><span data-stu-id="27c0d-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="27c0d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27c0d-132">See also</span></span>

- [<span data-ttu-id="27c0d-133">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="27c0d-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="27c0d-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="27c0d-134">Configuration File Schema</span></span>](../index.md)
