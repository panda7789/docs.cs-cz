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
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927185"
---
# <a name="assert-element"></a><span data-ttu-id="fdd83-102">\<Assert – > element</span><span class="sxs-lookup"><span data-stu-id="fdd83-102">\<assert> Element</span></span>
<span data-ttu-id="fdd83-103">Určuje, zda se má při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody zobrazit okno se zprávou. určuje také název souboru, do kterého budou zapsány zprávy.</span><span class="sxs-lookup"><span data-stu-id="fdd83-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="fdd83-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="fdd83-104">\<configuration></span></span>  
<span data-ttu-id="fdd83-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="fdd83-105">\<system.diagnostics></span></span>  
<span data-ttu-id="fdd83-106">\<assert></span><span class="sxs-lookup"><span data-stu-id="fdd83-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd83-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdd83-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdd83-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fdd83-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fdd83-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fdd83-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdd83-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fdd83-110">Attributes</span></span>  
  
|<span data-ttu-id="fdd83-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fdd83-111">Attribute</span></span>|<span data-ttu-id="fdd83-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd83-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="fdd83-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fdd83-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fdd83-114">Určuje, zda se má zobrazit okno se zprávou, když je metoda **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="fdd83-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="fdd83-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="fdd83-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="fdd83-116">Určuje název souboru, do kterého se má zpráva zapsat, pokud je hodnota **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="fdd83-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="fdd83-117">AssertUiEnabled – atribut</span><span class="sxs-lookup"><span data-stu-id="fdd83-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="fdd83-118">Value</span><span class="sxs-lookup"><span data-stu-id="fdd83-118">Value</span></span>|<span data-ttu-id="fdd83-119">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd83-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="fdd83-120">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="fdd83-120">Displays the message box.</span></span> <span data-ttu-id="fdd83-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="fdd83-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="fdd83-122">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="fdd83-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdd83-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fdd83-123">Child Elements</span></span>  
 <span data-ttu-id="fdd83-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdd83-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdd83-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fdd83-125">Parent Elements</span></span>  
  
|<span data-ttu-id="fdd83-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdd83-126">Element</span></span>|<span data-ttu-id="fdd83-127">Popis</span><span class="sxs-lookup"><span data-stu-id="fdd83-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fdd83-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdd83-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fdd83-129">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="fdd83-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd83-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdd83-130">Remarks</span></span>  
 <span data-ttu-id="fdd83-131">Oba atributy v rámci  **\<kontrolního elementu >** jsou nepovinné.</span><span class="sxs-lookup"><span data-stu-id="fdd83-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="fdd83-132">Okna se zprávou můžete zakázat bez určení souboru, do kterého se mají zprávy zapisovat, nebo můžete zadat soubor, do kterého se mají zapisovat zprávy, a nechat okna zpráv zapnutá.</span><span class="sxs-lookup"><span data-stu-id="fdd83-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdd83-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdd83-133">Example</span></span>  
 <span data-ttu-id="fdd83-134">Následující příklad ukazuje, jak zakázat zobrazování oken zpráv při volání metody **Debug. Assert** a zapsat zprávy do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="fdd83-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdd83-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdd83-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="fdd83-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="fdd83-136">Trace and Debug Settings Schema</span></span>](index.md)
