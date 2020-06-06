---
title: <Crst_DisableSpinWait> – element
ms.date: 04/18/2019
f1_keywords:
- Crst_DisableSpinWait
helpviewer_keywords:
- Crst_DisableSpinWait element
ms.openlocfilehash: 0683081183081e249b2a9c89e1a6a15f638fb339
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117640"
---
# <a name="crst_disablespinwait-element"></a><span data-ttu-id="0af89-102">\<Crst_DisableSpinWait> – element</span><span class="sxs-lookup"><span data-stu-id="0af89-102">\<Crst_DisableSpinWait> element</span></span>

<span data-ttu-id="0af89-103">Určuje, jestli se má v případě, že se má v případě, že je to zamýšlí, zakázat číselník čekání</span><span class="sxs-lookup"><span data-stu-id="0af89-103">Specifies whether to disable spin-waiting for a critical section when contended.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Crst_DisableSpinWait>**  
  
## <a name="syntax"></a><span data-ttu-id="0af89-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0af89-104">Syntax</span></span>  
  
```xml  
<Crst_DisableSpinWait enabled="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0af89-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0af89-105">Attributes and Elements</span></span>

<span data-ttu-id="0af89-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0af89-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0af89-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0af89-107">Attributes</span></span>  
  
|<span data-ttu-id="0af89-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0af89-108">Attribute</span></span>|<span data-ttu-id="0af89-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0af89-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0af89-110">**umožněn**</span><span class="sxs-lookup"><span data-stu-id="0af89-110">**enabled**</span></span>|<span data-ttu-id="0af89-111">Určuje, jestli jsou zakázané oddíly, které čekají na kritické, pokud jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="0af89-111">Specifies whether spin-waiting for critical sections when they are contended is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0af89-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0af89-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="0af89-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0af89-113">Value</span></span>|<span data-ttu-id="0af89-114">Description</span><span class="sxs-lookup"><span data-stu-id="0af89-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0af89-115">1</span><span class="sxs-lookup"><span data-stu-id="0af89-115">1</span></span>|<span data-ttu-id="0af89-116">Zakažte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="0af89-116">Disable spin-waiting when a critical section cannot be acquired.</span></span>|  
|<span data-ttu-id="0af89-117">0</span><span class="sxs-lookup"><span data-stu-id="0af89-117">0</span></span>|<span data-ttu-id="0af89-118">Nepovolujte číselník čekání, pokud nelze získat kritickou sekci.</span><span class="sxs-lookup"><span data-stu-id="0af89-118">Do not disable spin-waiting when a critical section cannot be acquired.</span></span> <span data-ttu-id="0af89-119">Toto je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="0af89-119">This is the default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0af89-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0af89-120">Child Elements</span></span>  
 <span data-ttu-id="0af89-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="0af89-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0af89-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0af89-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0af89-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="0af89-123">Element</span></span>|<span data-ttu-id="0af89-124">Description</span><span class="sxs-lookup"><span data-stu-id="0af89-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0af89-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0af89-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0af89-126">Obsahuje informace o různých nastaveních konfigurace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0af89-126">Contains information about various runtime configuration settings.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0af89-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="0af89-127">Example</span></span>  

<span data-ttu-id="0af89-128">Následující příklad v případě, že je to zamýšlí, zakáže v částech kritické čekání.</span><span class="sxs-lookup"><span data-stu-id="0af89-128">The following example disables spin-waiting in critical sections when contended.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Crst_DisableSpinWait enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0af89-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="0af89-129">See also</span></span>

- [<span data-ttu-id="0af89-130">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0af89-130">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0af89-131">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0af89-131">Configuration File Schema</span></span>](../index.md)
