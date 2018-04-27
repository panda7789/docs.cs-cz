---
title: x:ClassModifier – direktiva
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab6036ecb37bb80588a59b581af0b88fc83230a4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xclassmodifier-directive"></a><span data-ttu-id="65515-102">x:ClassModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="65515-102">x:ClassModifier Directive</span></span>
<span data-ttu-id="65515-103">Mění chování kompilace XAML při `x:Class` k dispozici je také.</span><span class="sxs-lookup"><span data-stu-id="65515-103">Modifies XAML compilation behavior when `x:Class` is also provided.</span></span> <span data-ttu-id="65515-104">Konkrétně, místo vytvoření částečné `class` má `Public` (výchozí), úroveň přístupu poskytnutého `x:Class` je vytvořena s `NotPublic` úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="65515-104">Specifically, instead of creating a partial `class` that has a `Public` access level (the default), the provided `x:Class` is created with a `NotPublic` access level.</span></span> <span data-ttu-id="65515-105">Toto chování ovlivňuje úroveň přístupu pro třídy v vygenerované sestavení.</span><span class="sxs-lookup"><span data-stu-id="65515-105">This behavior affects the access level for the class in the generated assemblies.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="65515-106">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="65515-106">XAML Attribute Usage</span></span>  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="65515-107">Hodnoty XAML</span><span class="sxs-lookup"><span data-stu-id="65515-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="65515-108">*NotPublic*</span><span class="sxs-lookup"><span data-stu-id="65515-108">*NotPublic*</span></span>|<span data-ttu-id="65515-109">S přesným řetězcem předat zadejte <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> se liší v závislosti na programovací jazyk kódu, který používáte.</span><span class="sxs-lookup"><span data-stu-id="65515-109">The exact string to pass to specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varies, depending on the code-behind programming language that you use.</span></span> <span data-ttu-id="65515-110">V části poznámky.</span><span class="sxs-lookup"><span data-stu-id="65515-110">See Remarks.</span></span>|  
  
## <a name="dependencies"></a><span data-ttu-id="65515-111">Závislosti</span><span class="sxs-lookup"><span data-stu-id="65515-111">Dependencies</span></span>  
 <span data-ttu-id="65515-112">[x: Class –](../../../docs/framework/xaml-services/x-class-directive.md) také je třeba zadat u stejného elementu, a tento element musí být kořenový element na stránce.</span><span class="sxs-lookup"><span data-stu-id="65515-112">[x:Class](../../../docs/framework/xaml-services/x-class-directive.md) must also be provided on the same element, and that element must be the root element in a page.</span></span> <span data-ttu-id="65515-113">Další informace najdete v tématu [ \[MS-XAML\] části 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="65515-113">For more information, see [\[MS-XAML\] Section 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65515-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65515-114">Remarks</span></span>  
 <span data-ttu-id="65515-115">Hodnota `x:ClassModifier` v rozhraní .NET Framework XAML Services využití se liší podle programovací jazyk.</span><span class="sxs-lookup"><span data-stu-id="65515-115">The value of `x:ClassModifier` in .NET Framework XAML Services usage varies by programming language.</span></span> <span data-ttu-id="65515-116">Řetězec, který má použít, závisí na tom, jak každý z těchto jazyků implementuje jeho <xref:System.CodeDom.Compiler.CodeDomProvider> a převaděče typů vrátí k definování významy pro <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, a jestli je tento jazyk velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="65515-116">The string to use depends on how each language implements its <xref:System.CodeDom.Compiler.CodeDomProvider> and the type converters it returns to define the meanings for <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> and <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, and whether that language is case sensitive.</span></span>  
  
-   <span data-ttu-id="65515-117">Pro jazyk C#, řetězec pro určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `internal`.</span><span class="sxs-lookup"><span data-stu-id="65515-117">For C#, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `internal`.</span></span>  
  
-   <span data-ttu-id="65515-118">Pro Microsoft Visual Basic .NET, řetězec pro určení <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> je `Friend`.</span><span class="sxs-lookup"><span data-stu-id="65515-118">For Microsoft Visual Basic .NET, the string to pass to designate <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> is `Friend`.</span></span>  
  
-   <span data-ttu-id="65515-119">Pro [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], neexistují žádné cíle podporující kompilování XAML; hodnotu předávání tedy neurčené.</span><span class="sxs-lookup"><span data-stu-id="65515-119">For [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], no targets exist that support compiling XAML; therefore, the value to pass is unspecified.</span></span>  
  
 <span data-ttu-id="65515-120">Můžete také zadat <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` v jazyce C#, `Public` v jazyce Visual Basic), nicméně zadání <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> je zřídka provést, protože <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> již je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="65515-120">You can also specify <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` in C#, `Public` in Visual Basic); however, specifying <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is infrequently done because <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> is already the default behavior.</span></span>  
  
 <span data-ttu-id="65515-121">Ostatní hodnoty s ekvivalentní uživatelského kódu úrovně přístupu omezení, jako například `private` v jazyce C#, nejsou důležité pro `x:ClassModifier` protože odkazy na vnořené třídy nejsou podporované v jazyce XAML a proto <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifikátor má stejný účinek.</span><span class="sxs-lookup"><span data-stu-id="65515-121">Other values with equivalent user code access-level restrictions, such as `private` in C#, are not relevant for `x:ClassModifier` because nested class references are not supported in XAML, and therefore, the <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modifier has the same effect.</span></span>  
  
## <a name="security-notes"></a><span data-ttu-id="65515-122">Poznámky k zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65515-122">Security Notes</span></span>  
 <span data-ttu-id="65515-123">Úroveň přístupu podle údajů v `x:ClassModifier` stále podléhá interpretace konkrétní architektury a jejich funkce.</span><span class="sxs-lookup"><span data-stu-id="65515-123">The access level as declared in `x:ClassModifier` is still subject to interpretation by particular frameworks and their capabilities.</span></span> <span data-ttu-id="65515-124">WPF obsahuje funkce pro načtení a vytvoření instance typy kde `x:ClassModifier` je `internal`v případě, že třídy se odkazuje z grafického subsystému WPF prostředku prostřednictvím balíčku identifikátor URI odkazu.</span><span class="sxs-lookup"><span data-stu-id="65515-124">WPF includes capabilities to load and instantiate types where `x:ClassModifier` is `internal`, if that class is referenced from a WPF resource through a pack URI reference.</span></span> <span data-ttu-id="65515-125">V důsledku tento případ a potenciálně jiné, jako je implementované ostatní platformy, nespoléhejte pouze na `x:ClassModifier` aby blokovat všechny možné konkretizaci pokusy o přihlášení.</span><span class="sxs-lookup"><span data-stu-id="65515-125">As a consequence of this case and potentially others like it implemented by other frameworks, do not rely exclusively on `x:ClassModifier` to block all possible instantiation attempts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65515-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="65515-126">See Also</span></span>  
 [<span data-ttu-id="65515-127">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="65515-127">x:Class Directive</span></span>](../../../docs/framework/xaml-services/x-class-directive.md)  
 [<span data-ttu-id="65515-128">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="65515-128">Code-Behind and XAML in WPF</span></span>](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [<span data-ttu-id="65515-129">x:FieldModifier – direktiva</span><span class="sxs-lookup"><span data-stu-id="65515-129">x:FieldModifier Directive</span></span>](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [<span data-ttu-id="65515-130">Zabezpečení (WPF)</span><span class="sxs-lookup"><span data-stu-id="65515-130">Security (WPF)</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="65515-131">Typy migrované z prostředí WPF do oboru názvů System.Xaml</span><span class="sxs-lookup"><span data-stu-id="65515-131">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
