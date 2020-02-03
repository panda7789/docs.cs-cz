---
title: Použití standardních typů výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743539"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="70357-102">Použití standardních typů výjimek</span><span class="sxs-lookup"><span data-stu-id="70357-102">Using Standard Exception Types</span></span>
<span data-ttu-id="70357-103">Tato část popisuje standardní výjimky poskytované rozhraním a podrobnosti o jejich použití.</span><span class="sxs-lookup"><span data-stu-id="70357-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="70357-104">Seznam není úplným způsobem vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="70357-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="70357-105">Informace o použití jiných typů výjimek rozhraní naleznete v referenční dokumentaci k .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="70357-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="70357-106">Výjimka a SystemException</span><span class="sxs-lookup"><span data-stu-id="70357-106">Exception and SystemException</span></span>
 <span data-ttu-id="70357-107">❌ nevyvolávat <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70357-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="70357-108">❌ nezachytí `System.Exception` nebo `System.SystemException` v kódu rozhraní, pokud se nechcete znovu vyvolat.</span><span class="sxs-lookup"><span data-stu-id="70357-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="70357-109">❌ zabránit zachycení `System.Exception` nebo `System.SystemException`, s výjimkou obslužných rutin výjimek nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="70357-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="70357-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="70357-110">ApplicationException</span></span>
 <span data-ttu-id="70357-111">❌ nevyvolávat nebo odvozovat z <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="70357-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="70357-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="70357-112">InvalidOperationException</span></span>
 <span data-ttu-id="70357-113">✔️ vyvolat <xref:System.InvalidOperationException>, pokud je objekt v nevhodném stavu.</span><span class="sxs-lookup"><span data-stu-id="70357-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="70357-114">ArgumentException, ArgumentNullException a ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="70357-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="70357-115">✔️ Vyvolejte <xref:System.ArgumentException> nebo jeden z jeho podtypů, pokud jsou do člena předány chybné argumenty.</span><span class="sxs-lookup"><span data-stu-id="70357-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="70357-116">Preferovat největší odvozený typ výjimky, je-li k dispozici.</span><span class="sxs-lookup"><span data-stu-id="70357-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="70357-117">✔️ nastavit vlastnost `ParamName` při vyvolání jedné z podtříd `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="70357-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="70357-118">Tato vlastnost představuje název parametru, který způsobil výjimku vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="70357-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="70357-119">Všimněte si, že vlastnost může být nastavena pomocí jednoho z přetížení konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="70357-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="70357-120">✔️ použít `value` pro název parametru implicitní hodnoty vlastností Setters.</span><span class="sxs-lookup"><span data-stu-id="70357-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="70357-121">NullReferenceException, IndexOutOfRangeException a AccessViolationException –</span><span class="sxs-lookup"><span data-stu-id="70357-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="70357-122">❌ neumožňují veřejně vyvolávat rozhraní API explicitně nebo implicitně volat <xref:System.NullReferenceException>, <xref:System.AccessViolationException>nebo <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="70357-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="70357-123">Tyto výjimky jsou vyhrazeny a vyvolány spouštěcím modulem a ve většině případů značí chybu.</span><span class="sxs-lookup"><span data-stu-id="70357-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="70357-124">Udělejte kontrolu argumentů, aby nedocházelo k vyvolání těchto výjimek.</span><span class="sxs-lookup"><span data-stu-id="70357-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="70357-125">Vyvolávání těchto výjimek zpřístupňuje podrobnosti o implementaci vaší metody, která se může v průběhu času měnit.</span><span class="sxs-lookup"><span data-stu-id="70357-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="70357-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="70357-126">StackOverflowException</span></span>
 <span data-ttu-id="70357-127">❌ explicitně negenerovat <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="70357-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="70357-128">Výjimka by měla být explicitně vyvolána pouze modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="70357-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="70357-129">❌ nezachytit `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="70357-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="70357-130">Není skoro možné psát spravovaný kód, který zůstává konzistentní v přítomnosti libovolného přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="70357-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="70357-131">Nespravované části CLR zůstávají konzistentní pomocí sond pro přesun přetečení zásobníku do dobře definovaných míst a nikoli z přetečení z libovolného zásobníku.</span><span class="sxs-lookup"><span data-stu-id="70357-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="70357-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="70357-132">OutOfMemoryException</span></span>
 <span data-ttu-id="70357-133">❌ explicitně negenerovat <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="70357-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="70357-134">Tato výjimka má být vyvolána pouze infrastrukturou CLR.</span><span class="sxs-lookup"><span data-stu-id="70357-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="70357-135">ComException, SEHException – a ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="70357-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="70357-136">❌ explicitně Nevolejte <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>a <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="70357-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="70357-137">Tyto výjimky mají být vyvolány pouze infrastrukturou CLR.</span><span class="sxs-lookup"><span data-stu-id="70357-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="70357-138">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="70357-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="70357-139">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="70357-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="70357-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="70357-140">See also</span></span>

- [<span data-ttu-id="70357-141">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="70357-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="70357-142">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="70357-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
