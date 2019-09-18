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
ms.openlocfilehash: 5daff0567c1b1415fe994f6e39b4079cb2ab7346
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053822"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="28052-102">x:ClassModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="28052-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="28052-103">V případě, že `x:Class` je k dispozici i chování kompilace XAML, upraví.</span><span class="sxs-lookup"><span data-stu-id="28052-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="28052-104">`class` Konkrétně místo vytvoření částečného, který `Public` má úroveň přístupu (výchozí nastavení), je `NotPublic` zadaný `x:Class` s úrovní přístupu.</span><span class="sxs-lookup"><span data-stu-id="28052-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="28052-105">Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="28052-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="28052-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="28052-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="28052-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="28052-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28052-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="28052-108">*NotPublic*</span></span>|<span data-ttu-id="28052-109">Přesný řetězec, který se má předat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> který se liší v závislosti na programovacím jazyku na pozadí, který používáte.</span><span class="sxs-lookup"><span data-stu-id="28052-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="28052-110">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="28052-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="28052-111">Závislosti</span><span class="sxs-lookup"><span data-stu-id="28052-111">Dependencies</span></span>  
 <span data-ttu-id="28052-112">[x:Class](x-class-directive.md) musí být také zadáno na stejném elementu a tento prvek musí být kořenovým elementem na stránce.</span><span class="sxs-lookup"><span data-stu-id="28052-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="28052-113">Další informace naleznete v [ \[části MS-XAML\] 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="28052-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28052-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="28052-114">Remarks</span></span>  
 <span data-ttu-id="28052-115">Hodnota `x:ClassModifier` v .NET Framework použití služeb XAML se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="28052-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="28052-116">Řetězec, který se má použít, závisí na tom, <xref:System.CodeDom.Compiler.CodeDomProvider> jak jednotlivé jazyky implementují své a konvertory typů, které <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> vrátí <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, aby definovali význam pro a a zda se u tohoto jazyka rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="28052-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="28052-117">Řetězec C#, který se má předat k určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> , `internal`je.</span><span class="sxs-lookup"><span data-stu-id="28052-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="28052-118">Pro Microsoft Visual Basic .NET je <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`řetězec, který se má předat, označovat.</span><span class="sxs-lookup"><span data-stu-id="28052-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="28052-119">Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML. Proto hodnota, která má být předána, není určena.</span><span class="sxs-lookup"><span data-stu-id="28052-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="28052-120"><xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Můžete také zadat (`public` v C#, `Public` v Visual Basic). zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je však nečasto provedeno, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozím chováním.</span><span class="sxs-lookup"><span data-stu-id="28052-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="28052-121">Další hodnoty s ekvivalentními omezeními na `private` úrovni uživatelského kódu, jako je například v C#, nejsou relevantní `x:ClassModifier` , protože vnořené odkazy na třídy nejsou <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> v jazyce XAML podporovány, a proto má modifikátor stejný účinek. .</span><span class="sxs-lookup"><span data-stu-id="28052-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="28052-122">Poznámky k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="28052-122">Security Notes</span></span>  
 <span data-ttu-id="28052-123">Úroveň přístupu, jak je uvedeno `x:ClassModifier` v, je stále předmětem výkladu konkrétních platforem a jejich schopností.</span><span class="sxs-lookup"><span data-stu-id="28052-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="28052-124">WPF obsahuje možnosti pro načtení a vytvoření instance typů, `x:ClassModifier` kde `internal`je, pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu identifikátoru URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="28052-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="28052-125">V důsledku tohoto případu a potenciálně jiným způsobem, jako je implementováno jinými rozhraními, nespoléhá výhradně na `x:ClassModifier` to, abyste zablokovali všechny možné pokusy o vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="28052-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28052-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28052-126">See also</span></span>

- [<span data-ttu-id="28052-127">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="28052-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="28052-128">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="28052-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="28052-129">x:FieldModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="28052-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="28052-130">Zabezpečení (WPF)</span><span class="sxs-lookup"><span data-stu-id="28052-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="28052-131">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="28052-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
