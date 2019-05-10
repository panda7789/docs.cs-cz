---
title: x:ClassModifier – direktiva
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: 8f90f56a595fa175d5c48a929fc19ceb81ab0d63
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617110"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="8ca8a-102">x:ClassModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="8ca8a-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="8ca8a-103">Upravuje chování kompilace XAML při `x:Class` je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="8ca8a-104">Konkrétně, místo vytvoření částečné `class` , který má `Public` (výchozí) úroveň přístupu zadaných `x:Class` se vytvoří s `NotPublic` úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="8ca8a-105">Toto chování má vliv na úroveň přístupu pro třídu v vygenerované sestavení.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="8ca8a-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="8ca8a-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="8ca8a-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="8ca8a-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ca8a-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="8ca8a-108">*NotPublic*</span></span>|<span data-ttu-id="8ca8a-109">Přesná předat zadejte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> oproti <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na použití modelu code-behind programovací jazyk, který používáte.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="8ca8a-110">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="8ca8a-111">Závislosti</span><span class="sxs-lookup"><span data-stu-id="8ca8a-111">Dependencies</span></span>  
 <span data-ttu-id="8ca8a-112">[x: Class](x-class-directive.md) musí se poskytnout i u stejného elementu, a tento element musí být kořenovým prvkem na stránce.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="8ca8a-113">Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="8ca8a-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ca8a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ca8a-114">Remarks</span></span>  
 <span data-ttu-id="8ca8a-115">Hodnota `x:ClassModifier` v rozhraní .NET Framework XAML Services využití se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="8ca8a-116">Řetězec, který má použít, závisí na způsob implementace každý jazyk jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a vrátí k definování význam pro typ převaděče <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je daný jazyk malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="8ca8a-117">Pro jazyk C#, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `internal`.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="8ca8a-118">Pro Microsoft Visual Basic .NET, řetězec, který má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `Friend`.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="8ca8a-119">Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], neexistují žádné cíle, které podporují kompilaci XAML; proto neurčená hodnotu pro předání.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="8ca8a-120">Můžete také určit <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v jazyce C#, `Public` v jazyce Visual Basic), nicméně zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zřídka dochází proto <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> již je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="8ca8a-121">Další hodnoty s ekvivalentní uživatelský kód úrovně přístupu omezení, jako například `private` v jazyce C#, nejsou relevantní pro `x:ClassModifier` protože odkazy na vnořené třídy nejsou podporovány v XAML a proto <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor má stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="8ca8a-122">Poznámky k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8ca8a-122">Security Notes</span></span>  
 <span data-ttu-id="8ca8a-123">Úroveň přístupu, jak je deklarován v `x:ClassModifier` stále podléhá interpretaci konkrétní rozhraní a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="8ca8a-124">WPF obsahuje funkce pro načtení a vytvoření instancí typů kde `x:ClassModifier` je `internal`, pokud tuto třídu se odkazuje z prostředku WPF prostřednictvím balíčku odkaz na identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="8ca8a-125">Následkem tohoto případu a potenciálně ostatní jako implementované další architektury, nespoléhejte pouze na `x:ClassModifier` blokování všech možných instance pokusí.</span><span class="sxs-lookup"><span data-stu-id="8ca8a-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca8a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ca8a-126">See also</span></span>

- [<span data-ttu-id="8ca8a-127">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="8ca8a-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="8ca8a-128">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="8ca8a-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="8ca8a-129">x:FieldModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="8ca8a-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="8ca8a-130">Zabezpečení (WPF)</span><span class="sxs-lookup"><span data-stu-id="8ca8a-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="8ca8a-131">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="8ca8a-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
