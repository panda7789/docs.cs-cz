---
title: '&lt;vyhodnocení&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b15e569ff6e42298c0a1de02f77ab7c302c70d86
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192678"
---
# <a name="ltassertgt-element"></a><span data-ttu-id="e6881-102">&lt;vyhodnocení&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="e6881-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="e6881-103">Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.</span><span class="sxs-lookup"><span data-stu-id="e6881-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="e6881-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e6881-104">\<configuration></span></span>  
<span data-ttu-id="e6881-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="e6881-105">\<system.diagnostics></span></span>  
<span data-ttu-id="e6881-106">\<vyhodnocení ></span><span class="sxs-lookup"><span data-stu-id="e6881-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6881-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6881-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6881-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6881-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e6881-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e6881-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6881-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6881-110">Attributes</span></span>  
  
|<span data-ttu-id="e6881-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e6881-111">Attribute</span></span>|<span data-ttu-id="e6881-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e6881-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="e6881-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e6881-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e6881-114">Určuje, zda chcete-li zobrazit zprávu pole při **Debug.Assert –** vyhodnotí jako metoda **false**.</span><span class="sxs-lookup"><span data-stu-id="e6881-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="e6881-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e6881-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e6881-116">Určuje název souboru pro zápis zprávy, když **Debug.Assert –** vyhodnotí jako **false**.</span><span class="sxs-lookup"><span data-stu-id="e6881-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="e6881-117">assertuienabled atribut</span><span class="sxs-lookup"><span data-stu-id="e6881-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="e6881-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e6881-118">Value</span></span>|<span data-ttu-id="e6881-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e6881-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e6881-120">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e6881-120">Displays the message box.</span></span> <span data-ttu-id="e6881-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="e6881-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e6881-122">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e6881-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6881-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6881-123">Child Elements</span></span>  
 <span data-ttu-id="e6881-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e6881-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6881-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e6881-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e6881-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6881-126">Element</span></span>|<span data-ttu-id="e6881-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e6881-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6881-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6881-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e6881-129">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e6881-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6881-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6881-130">Remarks</span></span>  
 <span data-ttu-id="e6881-131">Oba atributy v  **\<vyhodnocení >** elementu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="e6881-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="e6881-132">Zakážete okna se zprávou bez zadání soubor pro zápis zprávy, které mají, nebo můžete určit soubor k zapsání zprávy při opuštění zprávy pole povolená.</span><span class="sxs-lookup"><span data-stu-id="e6881-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6881-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6881-133">Example</span></span>  
 <span data-ttu-id="e6881-134">Následující příklad ukazuje, jak zakázat zobrazování okna se zprávou, když voláte **Debug.Assert –** a zápis zpráv do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="e6881-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6881-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6881-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="e6881-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e6881-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
