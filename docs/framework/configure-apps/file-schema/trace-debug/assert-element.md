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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088938"
---
# <a name="assert-element"></a><span data-ttu-id="1ef3c-102">Element \<assert></span><span class="sxs-lookup"><span data-stu-id="1ef3c-102">\<assert> Element</span></span>
<span data-ttu-id="1ef3c-103">Určuje, zda se má při volání metody zobrazit okno se zprávou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> . určuje také název souboru, do kterého budou zapsány zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="1ef3c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ef3c-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ef3c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ef3c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="1ef3c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ef3c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ef3c-107">Attributes</span></span>  
  
|<span data-ttu-id="1ef3c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ef3c-108">Attribute</span></span>|<span data-ttu-id="1ef3c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="1ef3c-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="1ef3c-110">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1ef3c-111">Určuje, zda se má zobrazit okno se zprávou, když je metoda **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="1ef3c-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="1ef3c-113">Určuje název souboru, do kterého se má zpráva zapsat, pokud je hodnota **Debug. Assert** vyhodnocena jako **false**.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="1ef3c-114">AssertUiEnabled – atribut</span><span class="sxs-lookup"><span data-stu-id="1ef3c-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="1ef3c-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1ef3c-115">Value</span></span>|<span data-ttu-id="1ef3c-116">Description</span><span class="sxs-lookup"><span data-stu-id="1ef3c-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="1ef3c-117">Zobrazí okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-117">Displays the message box.</span></span> <span data-ttu-id="1ef3c-118">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="1ef3c-119">Nezobrazuje okno se zprávou.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ef3c-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ef3c-120">Child Elements</span></span>  
 <span data-ttu-id="1ef3c-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="1ef3c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ef3c-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ef3c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1ef3c-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ef3c-123">Element</span></span>|<span data-ttu-id="1ef3c-124">Description</span><span class="sxs-lookup"><span data-stu-id="1ef3c-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1ef3c-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="1ef3c-126">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef3c-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ef3c-127">Remarks</span></span>  
 <span data-ttu-id="1ef3c-128">Oba atributy v **\<assert>** elementu jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="1ef3c-129">Okna se zprávou můžete zakázat bez určení souboru, do kterého se mají zprávy zapisovat, nebo můžete zadat soubor, do kterého se mají zapisovat zprávy, a nechat okna zpráv zapnutá.</span><span class="sxs-lookup"><span data-stu-id="1ef3c-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef3c-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ef3c-130">Example</span></span>  
 <span data-ttu-id="1ef3c-131">Následující příklad ukazuje, jak zakázat zobrazování oken zpráv při volání metody **Debug. Assert** a zapsat zprávy do `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="1ef3c-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ef3c-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ef3c-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="1ef3c-133">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="1ef3c-133">Trace and Debug Settings Schema</span></span>](index.md)
