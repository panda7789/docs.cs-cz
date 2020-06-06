---
title: Element <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: d1d29a37999a01f3e370897a1052f4f94435a218
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73116461"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="574bf-102">Element \<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="574bf-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="574bf-103">Určuje, zda modul CLR (Common Language Runtime) umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.</span><span class="sxs-lookup"><span data-stu-id="574bf-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="574bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="574bf-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="574bf-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="574bf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="574bf-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="574bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="574bf-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="574bf-107">Attributes</span></span>  
  
|<span data-ttu-id="574bf-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="574bf-108">Attribute</span></span>|<span data-ttu-id="574bf-109">Popis</span><span class="sxs-lookup"><span data-stu-id="574bf-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="574bf-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="574bf-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="574bf-111">Určuje, že aplikace bude zachytávat chyby při výjimkách poškozených stavů, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="574bf-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="574bf-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="574bf-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="574bf-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="574bf-113">Value</span></span>|<span data-ttu-id="574bf-114">Description</span><span class="sxs-lookup"><span data-stu-id="574bf-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="574bf-115">Aplikace nebude zachytit nepoškozená selhání výjimek stavu, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="574bf-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="574bf-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="574bf-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="574bf-117">Aplikace zachytí chyby výjimek nepoškozených stavů, jako je například porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="574bf-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="574bf-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="574bf-118">Child Elements</span></span>  
 <span data-ttu-id="574bf-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="574bf-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="574bf-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="574bf-120">Parent Elements</span></span>  
  
|<span data-ttu-id="574bf-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="574bf-121">Element</span></span>|<span data-ttu-id="574bf-122">Description</span><span class="sxs-lookup"><span data-stu-id="574bf-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="574bf-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="574bf-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="574bf-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="574bf-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="574bf-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="574bf-125">Remarks</span></span>  
 <span data-ttu-id="574bf-126">V .NET Framework verze 3,5 a starší používá modul common language runtime povolený spravovaný kód pro zachycení výjimek, které byly vyvolány poškozenými stavy procesu.</span><span class="sxs-lookup"><span data-stu-id="574bf-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="574bf-127">Příkladem tohoto typu výjimky je porušení přístupu.</span><span class="sxs-lookup"><span data-stu-id="574bf-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="574bf-128">Počínaje .NET Framework 4 spravovaný kód již nezachycuje tyto typy výjimek v `catch` blocích.</span><span class="sxs-lookup"><span data-stu-id="574bf-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="574bf-129">Tuto změnu však můžete přepsat a spravovat zpracování poškozených výjimek stavu dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="574bf-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="574bf-130">Nastavte `<legacyCorruptedStateExceptionsPolicy>` `enabled` atribut elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="574bf-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="574bf-131">Toto nastavení konfigurace se používá processwide a má vliv na všechny metody.</span><span class="sxs-lookup"><span data-stu-id="574bf-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="574bf-132">-nebo-</span><span class="sxs-lookup"><span data-stu-id="574bf-132">-or-</span></span>  
  
- <span data-ttu-id="574bf-133">Použijte <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> atribut na metodu, která obsahuje `catch` blok výjimek.</span><span class="sxs-lookup"><span data-stu-id="574bf-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="574bf-134">Tento prvek konfigurace je k dispozici pouze v .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="574bf-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="574bf-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="574bf-135">Example</span></span>  
 <span data-ttu-id="574bf-136">Následující příklad ukazuje, jak určit, že by se aplikace měla vrátit k chování před .NET Framework 4 a zachytit chyby výjimek všech poškozených stavů.</span><span class="sxs-lookup"><span data-stu-id="574bf-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="574bf-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="574bf-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="574bf-138">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="574bf-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="574bf-139">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="574bf-139">Configuration File Schema</span></span>](../index.md)
