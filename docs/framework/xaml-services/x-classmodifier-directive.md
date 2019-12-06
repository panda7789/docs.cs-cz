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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837230"
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="6cbc8-102">x:ClassModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="6cbc8-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="6cbc8-103">Upravuje chování kompilace XAML, pokud je k dispozici také `x:Class`.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="6cbc8-104">Konkrétně místo vytvoření částečného `class`, který má úroveň přístupu `Public` (výchozí nastavení), je zadaný `x:Class` vytvořen s úrovní přístupu `NotPublic`.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="6cbc8-105">Toto chování ovlivňuje úroveň přístupu pro třídu ve vygenerovaných sestaveních.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="6cbc8-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="6cbc8-106">XAML Attribute Usage</span></span>  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6cbc8-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="6cbc8-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cbc8-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="6cbc8-108">*NotPublic*</span></span>|<span data-ttu-id="6cbc8-109">Přesný řetězec, který má být předána <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na programovacím jazyku na pozadí, který používáte.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="6cbc8-110">Viz poznámky.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="6cbc8-111">Závislosti</span><span class="sxs-lookup"><span data-stu-id="6cbc8-111">Dependencies</span></span>  
 <span data-ttu-id="6cbc8-112">[x:Class](x-class-directive.md) musí být také zadáno na stejném elementu a tento prvek musí být kořenovým elementem na stránce.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-112">[x:Class](x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="6cbc8-113">Další informace naleznete v tématu [\[MS-XAML\] oddílu 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="6cbc8-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cbc8-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cbc8-114">Remarks</span></span>  
 <span data-ttu-id="6cbc8-115">Hodnota `x:ClassModifier` v .NET Framework použití služeb XAML se liší podle programovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="6cbc8-116">Řetězec, který se má použít, závisí na tom, jak jednotlivé jazyky implementují své <xref:System.CodeDom.Compiler.CodeDomProvider> a převaděče typu, které vrátí, aby definovali význam pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>a zda se u tohoto jazyka rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
- <span data-ttu-id="6cbc8-117">Řetězec C#, který se má předat určit <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, je `internal`.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
- <span data-ttu-id="6cbc8-118">Pro Microsoft Visual Basic .NET je řetězec, který se má předat, označit jako <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
- <span data-ttu-id="6cbc8-119">Pro C++/CLI neexistují žádné cíle, které podporují kompilaci XAML. Proto hodnota, která má být předána, není určena.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-119">For C++/CLI, no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="6cbc8-120">Můžete také zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v C#`Public` v Visual Basic); určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> však není často prováděno, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je již výchozím chováním.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="6cbc8-121">Jiné hodnoty s ekvivalentními omezeními na úrovni uživatelského kódu, jako je například C#`private` v, nejsou relevantní pro `x:ClassModifier`, protože vnořené odkazy na třídy nejsou v jazyce XAML podporovány a proto má modifikátor <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="6cbc8-122">Poznámky k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6cbc8-122">Security Notes</span></span>  
 <span data-ttu-id="6cbc8-123">Úroveň přístupu deklarovaná v `x:ClassModifier` stále podléhá výkladu konkrétními rozhraními a jejich schopnostmi.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="6cbc8-124">WPF obsahuje možnosti pro načtení a vytvoření instance typů, kde `x:ClassModifier` je `internal`, pokud je tato třída odkazována z prostředku WPF prostřednictvím odkazu na identifikátor URI balíčku.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="6cbc8-125">Jako důsledek tohoto případu a potenciálně jiné, jako je implementováno jinými rozhraními, nespoléhá výhradně na `x:ClassModifier` k blokování všech možných pokusů o vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="6cbc8-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cbc8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cbc8-126">See also</span></span>

- [<span data-ttu-id="6cbc8-127">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="6cbc8-127">x:Class Directive</span></span>](x-class-directive.md)
- [<span data-ttu-id="6cbc8-128">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="6cbc8-128">Code-Behind and XAML in WPF</span></span>](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="6cbc8-129">x:FieldModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="6cbc8-129">x:FieldModifier Directive</span></span>](x-fieldmodifier-directive.md)
- [<span data-ttu-id="6cbc8-130">Zabezpečení (WPF)</span><span class="sxs-lookup"><span data-stu-id="6cbc8-130">Security (WPF)</span></span>](../wpf/security-wpf.md)
- [<span data-ttu-id="6cbc8-131">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="6cbc8-131">Types Migrated from WPF to System.Xaml</span></span>](types-migrated-from-wpf-to-system-xaml.md)
