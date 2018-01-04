---
title: "Použití typů standardní výjimky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5098db5131c2e47c0b73efaac51477ef3b107761
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="0960c-102">Použití typů standardní výjimky</span><span class="sxs-lookup"><span data-stu-id="0960c-102">Using Standard Exception Types</span></span>
<span data-ttu-id="0960c-103">Tato část popisuje standardní výjimky poskytované rozhraní a podrobnosti o jejich využití.</span><span class="sxs-lookup"><span data-stu-id="0960c-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="0960c-104">V seznamu je rozhodně není vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="0960c-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="0960c-105">Naleznete na referenční dokumentaci rozhraní .NET Framework pro použití jiných typů výjimek Framework.</span><span class="sxs-lookup"><span data-stu-id="0960c-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="0960c-106">A SystemException – výjimka</span><span class="sxs-lookup"><span data-stu-id="0960c-106">Exception and SystemException</span></span>  
 <span data-ttu-id="0960c-107">**X nesmí** throw <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0960c-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="0960c-108">**X nesmí** catch `System.Exception` nebo `System.SystemException` v rámci kódu, pokud máte v úmyslu opětovné.</span><span class="sxs-lookup"><span data-stu-id="0960c-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="0960c-109">**X nepoužívejte** zachytávání `System.Exception` nebo `System.SystemException`, kromě obslužné rutiny výjimek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="0960c-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="0960c-110">ApplicationException –</span><span class="sxs-lookup"><span data-stu-id="0960c-110">ApplicationException</span></span>  
 <span data-ttu-id="0960c-111">**X nesmí** throw nebo jsou odvozeny od <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="0960c-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="0960c-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="0960c-112">InvalidOperationException</span></span>  
 <span data-ttu-id="0960c-113">**PROVEĎTE ✓** throw <xref:System.InvalidOperationException> Pokud objekt je v nevhodném stavu.</span><span class="sxs-lookup"><span data-stu-id="0960c-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="0960c-114">ArgumentException – ArgumentNullException a výjimka ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="0960c-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="0960c-115">**PROVEĎTE ✓** throw <xref:System.ArgumentException> nebo jednoho z jeho podtypech Pokud chybné argumenty jsou předány na člena.</span><span class="sxs-lookup"><span data-stu-id="0960c-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="0960c-116">Dáváte přednost nejodvozenějších typ výjimky, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0960c-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="0960c-117">**PROVEĎTE ✓** nastavit `ParamName` při vyvolání jeden podtříd `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="0960c-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="0960c-118">Tato vlastnost představuje název parametru, která způsobila vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="0960c-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="0960c-119">Všimněte si, že vlastnost lze nastavit pomocí jednoho z přetížení konstruktor.</span><span class="sxs-lookup"><span data-stu-id="0960c-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="0960c-120">**PROVEĎTE ✓** použít `value` pro název implicitní hodnota parametru nastavením vlastností.</span><span class="sxs-lookup"><span data-stu-id="0960c-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="0960c-121">NullReferenceException IndexOutOfRangeException a AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="0960c-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="0960c-122">**X nesmí** povolit veřejně možné volat rozhraní API pro explicitně nebo implicitně throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, nebo <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="0960c-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="0960c-123">Tyto výjimky jsou vyhrazené a vyvolané modul provádění a ve že většině případů se jednat o chybu.</span><span class="sxs-lookup"><span data-stu-id="0960c-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="0960c-124">Proveďte kontrolu nechcete-li tyto výjimky argumentu.</span><span class="sxs-lookup"><span data-stu-id="0960c-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="0960c-125">Vyvolání těchto výjimek zpřístupní podrobnosti implementace vaší metody, které můžou časem změnit.</span><span class="sxs-lookup"><span data-stu-id="0960c-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="0960c-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="0960c-126">StackOverflowException</span></span>  
 <span data-ttu-id="0960c-127">**X nesmí** explicitní generování <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="0960c-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="0960c-128">Pouze pomocí modulu CLR by měla být explicitně vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0960c-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="0960c-129">**X nesmí** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="0960c-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="0960c-130">Není možné téměř k zápisu spravovaného kódu, který konzistentní případě přetečení zásobníku libovolný.</span><span class="sxs-lookup"><span data-stu-id="0960c-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="0960c-131">Nespravované části modulu CLR zůstaly konzistentní s použitím sondy přesunout přetečení zásobníku na dobře definovaný místa, a nikoli zálohování z libovolné zásobníku některé.</span><span class="sxs-lookup"><span data-stu-id="0960c-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="0960c-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="0960c-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="0960c-133">**X nesmí** explicitní generování <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="0960c-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="0960c-134">Tato výjimka je vyvolána pouze pomocí infrastruktury CLR.</span><span class="sxs-lookup"><span data-stu-id="0960c-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="0960c-135">ComException SEHException – a ExecutionEngineException –</span><span class="sxs-lookup"><span data-stu-id="0960c-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="0960c-136">**X nesmí** explicitní generování <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, a <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="0960c-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="0960c-137">Tyto výjimky se mají být vyvolány pouze infrastruktury CLR.</span><span class="sxs-lookup"><span data-stu-id="0960c-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="0960c-138">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="0960c-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="0960c-139">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="0960c-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0960c-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="0960c-140">See Also</span></span>  
 [<span data-ttu-id="0960c-141">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="0960c-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="0960c-142">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="0960c-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
