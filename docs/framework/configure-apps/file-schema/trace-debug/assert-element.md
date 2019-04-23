---
title: Element <assert>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 2f3823265e358976f970cdfa36772d2251894280
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197604"
---
# <a name="assert-element"></a><span data-ttu-id="f6f0c-102">\<Assert – > – Element</span><span class="sxs-lookup"><span data-stu-id="f6f0c-102">\<assert> Element</span></span>
<span data-ttu-id="f6f0c-103">Určuje, jestli se má zobrazit okno se zprávou, když zavoláte <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zpráv do.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="f6f0c-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f6f0c-104">\<configuration></span></span>  
<span data-ttu-id="f6f0c-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="f6f0c-105">\<system.diagnostics></span></span>  
<span data-ttu-id="f6f0c-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="f6f0c-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6f0c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6f0c-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6f0c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6f0c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f6f0c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6f0c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6f0c-110">Attributes</span></span>  
  
|<span data-ttu-id="f6f0c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6f0c-111">Attribute</span></span>|<span data-ttu-id="f6f0c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f6f0c-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="f6f0c-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f6f0c-114">Určuje, zda chcete-li zobrazit zprávu pole při **Debug.Assert –** vyhodnotí jako metoda **false**.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="f6f0c-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f6f0c-116">Určuje název souboru pro zápis zprávy, když **Debug.Assert –** vyhodnotí jako **false**.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="f6f0c-117">assertuienabled atribut</span><span class="sxs-lookup"><span data-stu-id="f6f0c-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="f6f0c-118">Value</span><span class="sxs-lookup"><span data-stu-id="f6f0c-118">Value</span></span>|<span data-ttu-id="f6f0c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f6f0c-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="f6f0c-120">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-120">Displays the message box.</span></span> <span data-ttu-id="f6f0c-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="f6f0c-122">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6f0c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6f0c-123">Child Elements</span></span>  
 <span data-ttu-id="f6f0c-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6f0c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6f0c-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6f0c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f6f0c-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6f0c-126">Element</span></span>|<span data-ttu-id="f6f0c-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f6f0c-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6f0c-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f6f0c-129">Určuje, kteří shromažďování, ukládání a směrovat zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6f0c-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6f0c-130">Remarks</span></span>  
 <span data-ttu-id="f6f0c-131">Oba atributy v  **\<vyhodnocení >** elementu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="f6f0c-132">Zakážete okna se zprávou bez zadání soubor pro zápis zprávy, které mají, nebo můžete určit soubor k zapsání zprávy při opuštění zprávy pole povolená.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f0c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6f0c-133">Example</span></span>  
 <span data-ttu-id="f6f0c-134">Následující příklad ukazuje, jak zakázat zobrazování okna se zprávou, když voláte **Debug.Assert –** a zápis zpráv do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="f6f0c-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6f0c-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6f0c-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="f6f0c-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="f6f0c-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
