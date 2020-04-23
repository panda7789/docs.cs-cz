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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072030"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="24a9b-102">x:ClassModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="24a9b-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="24a9b-103">Upravuje chování kompilace XAML, pokud `x:Class` je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="24a9b-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="24a9b-104">Konkrétně namísto vytvoření `class` částečné, `Public` který má úroveň přístupu `x:Class` (výchozí), `NotPublic` za předpokladu, je vytvořen s úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="24a9b-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="24a9b-105">Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="24a9b-105">This behavior affects the access level for the class in the generated assemblies.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="24a9b-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="24a9b-106">XAML Attribute Usage</span></span>

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a><span data-ttu-id="24a9b-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="24a9b-107">XAML Values</span></span>

|||
|-|-|
|<span data-ttu-id="24a9b-108">*Není veřejná*</span><span class="sxs-lookup"><span data-stu-id="24a9b-108">*NotPublic*</span></span>|<span data-ttu-id="24a9b-109">Přesný řetězec předat zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> versus se liší v závislosti na kód na pozadí programovací jazyk, který používáte.</span><span class="sxs-lookup"><span data-stu-id="24a9b-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="24a9b-110">Viz Poznámky.</span><span class="sxs-lookup"><span data-stu-id="24a9b-110">See Remarks.</span></span>|

## <a name="dependencies"></a><span data-ttu-id="24a9b-111">Závislosti</span><span class="sxs-lookup"><span data-stu-id="24a9b-111">Dependencies</span></span>

<span data-ttu-id="24a9b-112">[x:Class](xclass-directive.md) musí být také k dispozici na stejný prvek a tento prvek musí být kořenový prvek na stránce.</span><span class="sxs-lookup"><span data-stu-id="24a9b-112">[x:Class](xclass-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="24a9b-113">Další informace naleznete [ \[v oddíle\] 4.3.1.8 ms-XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="24a9b-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>

## <a name="remarks"></a><span data-ttu-id="24a9b-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24a9b-114">Remarks</span></span>

<span data-ttu-id="24a9b-115">Hodnota `x:ClassModifier` v .NET XAML Services využití se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="24a9b-115">The value of `x:ClassModifier` in .NET XAML Services usage varies by programming language.</span></span> <span data-ttu-id="24a9b-116">Řetězec, který chcete použít, závisí <xref:System.CodeDom.Compiler.CodeDomProvider> na tom, jak každý jazyk implementuje jeho a převaděče typu, který vrátí k definování významů pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a zda je tento jazyk rozlišována malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="24a9b-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>

- <span data-ttu-id="24a9b-117">Pro C#, řetězec předat <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> k `internal`označení je .</span><span class="sxs-lookup"><span data-stu-id="24a9b-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>

- <span data-ttu-id="24a9b-118">V jazyce Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`je řetězec, který má být určen, .</span><span class="sxs-lookup"><span data-stu-id="24a9b-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>

- <span data-ttu-id="24a9b-119">Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML; proto hodnota předat není zadán.</span><span class="sxs-lookup"><span data-stu-id="24a9b-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>

<span data-ttu-id="24a9b-120">Můžete také <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zadat`public` ( v `Public` jazyce C#, v jazyce Visual Basic); však zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> se zřídka provádí, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="24a9b-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>

<span data-ttu-id="24a9b-121">Jiné hodnoty s ekvivalentní omezení přístupové `private` úrovně uživatelského kódu, `x:ClassModifier` například v c#, nejsou relevantní, protože vnořené odkazy na třídy nejsou v XAML podporovány, a proto má <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="24a9b-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>

## <a name="security-notes"></a><span data-ttu-id="24a9b-122">Bezpečnostní poznámky</span><span class="sxs-lookup"><span data-stu-id="24a9b-122">Security Notes</span></span>

<span data-ttu-id="24a9b-123">Úroveň přístupu uvedená v `x:ClassModifier` písmenu a) je stále předmětem výkladu konkrétními rámci a jejich schopnostmi.</span><span class="sxs-lookup"><span data-stu-id="24a9b-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="24a9b-124">WPF zahrnuje možnosti načíst a `x:ClassModifier` vytvořit `internal`instanci typů, kde je , pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="24a9b-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="24a9b-125">V důsledku tohoto případu a potenciálně dalších, jako je implementováno `x:ClassModifier` jinými rámci, se nespoléhají výhradně na blokování všech možných pokusů o vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="24a9b-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>

## <a name="see-also"></a><span data-ttu-id="24a9b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="24a9b-126">See also</span></span>

- [<span data-ttu-id="24a9b-127">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="24a9b-127">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="24a9b-128">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="24a9b-128">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="24a9b-129">x:FieldModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="24a9b-129">x:FieldModifier Directive</span></span>](xfieldmodifier-directive.md)
- [<span data-ttu-id="24a9b-130">Zabezpečení (WPF)</span><span class="sxs-lookup"><span data-stu-id="24a9b-130">Security (WPF)</span></span>](../../framework/wpf/security-wpf.md)
- [<span data-ttu-id="24a9b-131">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="24a9b-131">Types Migrated from WPF to System.Xaml</span></span>](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
