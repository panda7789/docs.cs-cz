---
title: Použití standardních typů výjimek
description: Přečtěte si o standardních typech výjimek v rozhraní .NET. Přečtěte si o SystemException, ApplicationException, ArgumentException, ComException a dalších.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663054"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="0d33e-104">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="0d33e-104">Using Standard Exception Types</span></span>
<span data-ttu-id="0d33e-105">Tato část popisuje standardní výjimky poskytované rozhraním a podrobnosti o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="0d33e-105">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="0d33e-106">Seznam není úplným způsobem vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="0d33e-106">The list is by no means exhaustive.</span></span> <span data-ttu-id="0d33e-107">Informace o použití jiných typů výjimek rozhraní naleznete v referenční dokumentaci k .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d33e-107">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="0d33e-108">Výjimka a SystemException</span><span class="sxs-lookup"><span data-stu-id="0d33e-108">Exception and SystemException</span></span>
 <span data-ttu-id="0d33e-109">❌Nevolejte <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-109">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="0d33e-110">❌Nepoužívejte zachycení `System.Exception` nebo `System.SystemException` v kódu architektury, pokud nechcete znovu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="0d33e-110">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="0d33e-111">❌Vyhněte se zachytávání `System.Exception` nebo `System.SystemException` , s výjimkou obslužných rutin výjimek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="0d33e-111">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="0d33e-112">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="0d33e-112">ApplicationException</span></span>
 <span data-ttu-id="0d33e-113">❌Negenerovat nebo odvozovat z <xref:System.ApplicationException> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-113">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="0d33e-114">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="0d33e-114">InvalidOperationException</span></span>
 <span data-ttu-id="0d33e-115">✔️ vyvolat, <xref:System.InvalidOperationException> Pokud je objekt v nevhodném stavu.</span><span class="sxs-lookup"><span data-stu-id="0d33e-115">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="0d33e-116">ArgumentException, ArgumentNullException a ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="0d33e-116">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="0d33e-117">✔️ throw <xref:System.ArgumentException> nebo jedno z jeho podtypů, pokud jsou do člena předány chybné argumenty.</span><span class="sxs-lookup"><span data-stu-id="0d33e-117">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="0d33e-118">Preferovat největší odvozený typ výjimky, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0d33e-118">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="0d33e-119">✔️ Nastavte `ParamName` vlastnost při vyvolání jedné z podtříd třídy `ArgumentException` .</span><span class="sxs-lookup"><span data-stu-id="0d33e-119">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="0d33e-120">Tato vlastnost představuje název parametru, který způsobil výjimku vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="0d33e-120">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="0d33e-121">Všimněte si, že vlastnost může být nastavena pomocí jednoho z přetížení konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0d33e-121">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="0d33e-122">✔️ použít `value` pro název parametru implicitní hodnoty pro nastavení vlastností.</span><span class="sxs-lookup"><span data-stu-id="0d33e-122">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="0d33e-123">NullReferenceException, IndexOutOfRangeException a AccessViolationException –</span><span class="sxs-lookup"><span data-stu-id="0d33e-123">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="0d33e-124">❌Nepovolujte veřejně vyvolávatná rozhraní API pro explicitní nebo implicitní vyvolání <xref:System.NullReferenceException> , <xref:System.AccessViolationException> nebo <xref:System.IndexOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-124">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="0d33e-125">Tyto výjimky jsou vyhrazeny a vyvolány spouštěcím modulem a ve většině případů značí chybu.</span><span class="sxs-lookup"><span data-stu-id="0d33e-125">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="0d33e-126">Udělejte kontrolu argumentů, aby nedocházelo k vyvolání těchto výjimek.</span><span class="sxs-lookup"><span data-stu-id="0d33e-126">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="0d33e-127">Vyvolávání těchto výjimek zpřístupňuje podrobnosti o implementaci vaší metody, která se může v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="0d33e-127">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="0d33e-128">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="0d33e-128">StackOverflowException</span></span>
 <span data-ttu-id="0d33e-129">❌Nevolejte explicitně <xref:System.StackOverflowException> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-129">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="0d33e-130">Výjimka by měla být explicitně vyvolána pouze modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="0d33e-130">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="0d33e-131">❌Nezachytit `StackOverflowException` .</span><span class="sxs-lookup"><span data-stu-id="0d33e-131">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="0d33e-132">Není skoro možné psát spravovaný kód, který zůstává konzistentní v přítomnosti libovolného přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0d33e-132">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="0d33e-133">Nespravované části CLR zůstávají konzistentní pomocí sond pro přesun přetečení zásobníku do dobře definovaných míst a nikoli z přetečení z libovolného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0d33e-133">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="0d33e-134">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="0d33e-134">OutOfMemoryException</span></span>
 <span data-ttu-id="0d33e-135">❌Nevolejte explicitně <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-135">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="0d33e-136">Tato výjimka má být vyvolána pouze infrastrukturou CLR.</span><span class="sxs-lookup"><span data-stu-id="0d33e-136">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="0d33e-137">ComException, SEHException – a ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="0d33e-137">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="0d33e-138">❌Nevolejte explicitně <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> a <xref:System.Runtime.InteropServices.SEHException> .</span><span class="sxs-lookup"><span data-stu-id="0d33e-138">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="0d33e-139">Tyto výjimky mají být vyvolány pouze infrastrukturou CLR.</span><span class="sxs-lookup"><span data-stu-id="0d33e-139">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="0d33e-140">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="0d33e-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="0d33e-141">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="0d33e-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="0d33e-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d33e-142">See also</span></span>

- [<span data-ttu-id="0d33e-143">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="0d33e-143">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="0d33e-144">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="0d33e-144">Design Guidelines for Exceptions</span></span>](exceptions.md)
