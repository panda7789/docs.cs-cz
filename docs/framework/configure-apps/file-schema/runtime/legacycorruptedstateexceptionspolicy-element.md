---
title: Element <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116461"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="8aa64-102">\<element > legacyCorruptedStateExceptionsPolicy</span><span class="sxs-lookup"><span data-stu-id="8aa64-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="8aa64-103">Určuje, zda modul CLR (Common Language Runtime) umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="8aa64-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8aa64-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8aa64-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="8aa64-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="8aa64-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy >**</span><span class="sxs-lookup"><span data-stu-id="8aa64-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa64-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aa64-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa64-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8aa64-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8aa64-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8aa64-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa64-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8aa64-110">Attributes</span></span>  
  
|<span data-ttu-id="8aa64-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8aa64-111">Attribute</span></span>|<span data-ttu-id="8aa64-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8aa64-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="8aa64-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="8aa64-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="8aa64-114">Určuje, že aplikace bude zachytávat chyby při výjimkách poškozených stavů, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8aa64-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="8aa64-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="8aa64-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8aa64-116">Value</span></span>|<span data-ttu-id="8aa64-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8aa64-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="8aa64-118">Aplikace nebude zachytit nepoškozená selhání výjimek stavu, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="8aa64-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="8aa64-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="8aa64-120">Aplikace zachytí chyby výjimek nepoškozených stavů, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa64-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8aa64-121">Child Elements</span></span>  
 <span data-ttu-id="8aa64-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8aa64-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa64-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8aa64-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa64-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8aa64-124">Element</span></span>|<span data-ttu-id="8aa64-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8aa64-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8aa64-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8aa64-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8aa64-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="8aa64-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa64-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8aa64-128">Remarks</span></span>  
 <span data-ttu-id="8aa64-129">V .NET Framework verze 3,5 a starší používá modul common language runtime povolený spravovaný kód pro zachycení výjimek, které byly vyvolány poškozenými stavy procesu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="8aa64-130">Příkladem tohoto typu výjimky je porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="8aa64-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="8aa64-131">Počínaje .NET Framework 4 spravovaný kód již nezachycuje tyto typy výjimek v blocích `catch`.</span><span class="sxs-lookup"><span data-stu-id="8aa64-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="8aa64-132">Tuto změnu však můžete přepsat a spravovat zpracování poškozených výjimek stavu dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="8aa64-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="8aa64-133">Nastavte atribut `enabled` elementu `<legacyCorruptedStateExceptionsPolicy>` na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="8aa64-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="8aa64-134">Toto nastavení konfigurace se používá processwide a má vliv na všechny metody.</span><span class="sxs-lookup"><span data-stu-id="8aa64-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="8aa64-135">-nebo-</span><span class="sxs-lookup"><span data-stu-id="8aa64-135">-or-</span></span>  
  
- <span data-ttu-id="8aa64-136">Použijte atribut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> pro metodu, která obsahuje blok `catch` Exceptions.</span><span class="sxs-lookup"><span data-stu-id="8aa64-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="8aa64-137">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="8aa64-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8aa64-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="8aa64-138">Example</span></span>  
 <span data-ttu-id="8aa64-139">Následující příklad ukazuje, jak určit, že by se aplikace měla vrátit k chování před .NET Framework 4 a zachytit chyby výjimek všech poškozených stavů.</span><span class="sxs-lookup"><span data-stu-id="8aa64-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8aa64-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8aa64-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="8aa64-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="8aa64-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8aa64-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="8aa64-142">Configuration File Schema</span></span>](../index.md)
