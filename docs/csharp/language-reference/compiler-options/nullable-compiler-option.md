---
title: -Nullable (možnosti kompilátoru C#)
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: a68255dba18a022784cd4aaf0027c371893c577b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84449811"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="b4fee-102">-Nullable (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b4fee-102">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="b4fee-103">Možnost **-Nullable** umožňuje zadat požadovaný kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-103">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4fee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4fee-104">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="b4fee-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b4fee-105">Arguments</span></span>

<span data-ttu-id="b4fee-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="b4fee-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="b4fee-107">Zadáním `+` nebo pouhou **možnou hodnotou null**způsobí, že kompilátor povolí kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-107">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="b4fee-108">Určení `-` , které platí v případě, že neurčíte **hodnotu**null, zakážete kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-108">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="b4fee-109">`enable`&#124; `disable` &#124; `warnings` &#124;`annotations`</span><span class="sxs-lookup"><span data-stu-id="b4fee-109">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="b4fee-110">Určuje možnost kontextu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-110">Specifies the nullable context option.</span></span> <span data-ttu-id="b4fee-111">Podobně jako `+` nebo `-` , pokud chcete povolit a zakázat, ale umožňuje více členitosti kontextu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-111">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="b4fee-112">`enable`Argument, který je platný, jako Pokud zadáte **hodnotu null**, povoluje kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-112">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="b4fee-113">Při zadání `disable` se zakáže kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-113">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="b4fee-114">Při zadání `warnings` argumentu **-Nullable:** Warnings je povolený kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-114">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="b4fee-115">Při zadávání `annotations` argumentu **-Nullable: Annotations**je povolený kontext anotace s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b4fee-115">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4fee-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4fee-116">Remarks</span></span>

<span data-ttu-id="b4fee-117">Analýza toku se používá k odvození hodnoty null proměnných v rámci spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="b4fee-117">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="b4fee-118">Odvozená hodnota null proměnné je nezávislá na deklarované hodnotě null proměnné.</span><span class="sxs-lookup"><span data-stu-id="b4fee-118">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="b4fee-119">Volání metod jsou analyzována i v případě, že jsou podmíněně vynechána.</span><span class="sxs-lookup"><span data-stu-id="b4fee-119">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="b4fee-120">Například <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> v režimu vydání.</span><span class="sxs-lookup"><span data-stu-id="b4fee-120">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="b4fee-121">Vyvolání metod popsaných s následujícími atributy ovlivní také analýzu toků:</span><span class="sxs-lookup"><span data-stu-id="b4fee-121">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="b4fee-122">Jednoduché předběžné podmínky: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> a<xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="b4fee-122">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="b4fee-123">Jednoduché následné stavy: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> a<xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="b4fee-123">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="b4fee-124">Podmíněné následné podmínky: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> a<xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="b4fee-124">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="b4fee-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute>(např. `DoesNotReturnIf(false)` pro <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) a<xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="b4fee-125"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (e.g. `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="b4fee-126">Stavy po členu: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> a<xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="b4fee-126">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="b4fee-127">Nastavení této možnosti kompilátoru v projektu</span><span class="sxs-lookup"><span data-stu-id="b4fee-127">To set this compiler option in a project</span></span>

<span data-ttu-id="b4fee-128">Úpravou *. csproj* přidejte `<Nullable>` značku v `Project/PropertyGroup` hierarchii:</span><span class="sxs-lookup"><span data-stu-id="b4fee-128">Edit the *.csproj* to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="b4fee-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4fee-129">See also</span></span>

- [<span data-ttu-id="b4fee-130">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="b4fee-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b4fee-131">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b4fee-131">Nullable reference types</span></span>](../../nullable-references.md)
