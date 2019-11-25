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
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088938"
---
# <a name="assert-element"></a><span data-ttu-id="e2142-102">\<Assert > elementu</span><span class="sxs-lookup"><span data-stu-id="e2142-102">\<assert> Element</span></span>
<span data-ttu-id="e2142-103">Určuje, zda se má při volání metody <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> zobrazit okno se zprávou. Určuje také název souboru, do kterého se mají zapisovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="e2142-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

<span data-ttu-id="e2142-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e2142-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2142-105">&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2142-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="e2142-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<assert >**</span><span class="sxs-lookup"><span data-stu-id="e2142-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e2142-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2142-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2142-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2142-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2142-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2142-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2142-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2142-110">Attributes</span></span>  
  
|<span data-ttu-id="e2142-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="e2142-111">Attribute</span></span>|<span data-ttu-id="e2142-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e2142-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="e2142-113">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e2142-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e2142-114">Určuje, zda se má zobrazit okno se zprávou, když je metoda **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="e2142-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="e2142-115">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="e2142-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e2142-116">Určuje název souboru, do kterého se má zpráva zapsat, pokud je hodnota **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="e2142-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="e2142-117">AssertUiEnabled – atribut</span><span class="sxs-lookup"><span data-stu-id="e2142-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="e2142-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e2142-118">Value</span></span>|<span data-ttu-id="e2142-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e2142-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="e2142-120">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e2142-120">Displays the message box.</span></span> <span data-ttu-id="e2142-121">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="e2142-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="e2142-122">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e2142-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2142-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2142-123">Child Elements</span></span>  
 <span data-ttu-id="e2142-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2142-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2142-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2142-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e2142-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2142-126">Element</span></span>|<span data-ttu-id="e2142-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e2142-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e2142-128">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2142-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e2142-129">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e2142-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2142-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2142-130">Remarks</span></span>  
 <span data-ttu-id="e2142-131">Oba atributy v **\<assert >** elementu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="e2142-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="e2142-132">Okna se zprávou můžete zakázat bez určení souboru, do kterého se mají zprávy zapisovat, nebo můžete zadat soubor, do kterého se mají zapisovat zprávy, a nechat okna zpráv zapnutá.</span><span class="sxs-lookup"><span data-stu-id="e2142-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2142-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2142-133">Example</span></span>  
 <span data-ttu-id="e2142-134">Následující příklad ukazuje, jak zakázat zobrazování oken zpráv při volání metody **Debug. Assert** a zapsat zprávy do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="e2142-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e2142-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2142-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e2142-136">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e2142-136">Trace and Debug Settings Schema</span></span>](index.md)
