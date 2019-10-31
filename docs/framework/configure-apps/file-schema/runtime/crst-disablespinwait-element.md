---
title: < element > Crst_DisableSpinWait
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117640"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="388d2-102">\<element > Crst_DisableSpinWait</span><span class="sxs-lookup"><span data-stu-id="388d2-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="388d2-103">Určuje, jestli se má v případě, že se má v případě, že je to zamýšlí, zakázat číselník čekání</span><span class="sxs-lookup"><span data-stu-id="388d2-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
<span data-ttu-id="388d2-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="388d2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="388d2-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="388d2-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="388d2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Crst_DisableSpinWait >**</span><span class="sxs-lookup"><span data-stu-id="388d2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="388d2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="388d2-107">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="388d2-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="388d2-108">Attributes and Elements</span></span>

<span data-ttu-id="388d2-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="388d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="388d2-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="388d2-110">Attributes</span></span>  
  
|<span data-ttu-id="388d2-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="388d2-111">Attribute</span></span>|<span data-ttu-id="388d2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="388d2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="388d2-113">**umožněn**</span><span class="sxs-lookup"><span data-stu-id="388d2-113">**enabled**</span></span>|<span data-ttu-id="388d2-114">Určuje, jestli jsou zakázané oddíly, které čekají na kritické, pokud jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="388d2-114">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="388d2-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="388d2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="388d2-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="388d2-116">Value</span></span>|<span data-ttu-id="388d2-117">Popis</span><span class="sxs-lookup"><span data-stu-id="388d2-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="388d2-118">první</span><span class="sxs-lookup"><span data-stu-id="388d2-118">1</span></span>|<span data-ttu-id="388d2-119">Zakažte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="388d2-119">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="388d2-120">0,8</span><span class="sxs-lookup"><span data-stu-id="388d2-120">0</span></span>|<span data-ttu-id="388d2-121">Nepovolujte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="388d2-121">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="388d2-122">Jedná se o výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="388d2-122">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="388d2-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="388d2-123">Child Elements</span></span>  
 <span data-ttu-id="388d2-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="388d2-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="388d2-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="388d2-125">Parent Elements</span></span>  
  
|<span data-ttu-id="388d2-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="388d2-126">Element</span></span>|<span data-ttu-id="388d2-127">Popis</span><span class="sxs-lookup"><span data-stu-id="388d2-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="388d2-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="388d2-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="388d2-129">Obsahuje informace o různých nastaveních konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="388d2-129">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="388d2-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="388d2-130">Example</span></span>  

<span data-ttu-id="388d2-131">Následující příklad v případě, že je to zamýšlí, zakáže v částech kritické čekání.</span><span class="sxs-lookup"><span data-stu-id="388d2-131">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="388d2-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="388d2-132">See also</span></span>

- [<span data-ttu-id="388d2-133">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="388d2-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="388d2-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="388d2-134">Configuration File Schema</span></span>](../index.md)
