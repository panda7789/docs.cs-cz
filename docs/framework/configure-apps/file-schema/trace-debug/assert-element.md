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
ms.openlocfilehash: 43a3b4ea9d953d9dbb7a98c8481185ddc7e4d674
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701947"
---
# <a name="ltassertgt-element"></a><span data-ttu-id="5a463-102">&lt;vyhodnocení&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="5a463-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="5a463-103">Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.</span><span class="sxs-lookup"><span data-stu-id="5a463-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="5a463-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5a463-104">\<configuration></span></span>  
<span data-ttu-id="5a463-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="5a463-105">\<system.diagnostics></span></span>  
<span data-ttu-id="5a463-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="5a463-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a463-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a463-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a463-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a463-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a463-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5a463-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a463-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a463-110">Attributes</span></span>  
  
|<span data-ttu-id="5a463-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a463-111">Attribute</span></span>|<span data-ttu-id="5a463-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5a463-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="5a463-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a463-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5a463-114">Určuje, zda chcete-li zobrazit zprávu pole při **Debug.Assert –** vyhodnotí jako metoda **false**.</span><span class="sxs-lookup"><span data-stu-id="5a463-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="5a463-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="5a463-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="5a463-116">Určuje název souboru pro zápis zprávy, když **Debug.Assert –** vyhodnotí jako **false**.</span><span class="sxs-lookup"><span data-stu-id="5a463-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="5a463-117">assertuienabled atribut</span><span class="sxs-lookup"><span data-stu-id="5a463-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="5a463-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a463-118">Value</span></span>|<span data-ttu-id="5a463-119">Popis</span><span class="sxs-lookup"><span data-stu-id="5a463-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="5a463-120">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="5a463-120">Displays the message box.</span></span> <span data-ttu-id="5a463-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="5a463-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="5a463-122">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="5a463-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a463-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a463-123">Child Elements</span></span>  
 <span data-ttu-id="5a463-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a463-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a463-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a463-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5a463-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a463-126">Element</span></span>|<span data-ttu-id="5a463-127">Popis</span><span class="sxs-lookup"><span data-stu-id="5a463-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a463-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a463-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5a463-129">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="5a463-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a463-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a463-130">Remarks</span></span>  
 <span data-ttu-id="5a463-131">Oba atributy v  **\<vyhodnocení >** elementu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="5a463-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="5a463-132">Zakážete okna se zprávou bez zadání soubor pro zápis zprávy, které mají, nebo můžete určit soubor k zapsání zprávy při opuštění zprávy pole povolená.</span><span class="sxs-lookup"><span data-stu-id="5a463-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a463-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a463-133">Example</span></span>  
 <span data-ttu-id="5a463-134">Následující příklad ukazuje, jak zakázat zobrazování okna se zprávou, když voláte **Debug.Assert –** a zápis zpráv do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="5a463-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a463-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a463-135">See also</span></span>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="5a463-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="5a463-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
