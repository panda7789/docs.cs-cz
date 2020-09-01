---
description: -Nullable (možnosti kompilátoru C#)
title: -Nullable (možnosti kompilátoru C#)
author: IEvangelist
ms.author: dapine
ms.date: 06/04/2020
f1_keywords:
- /nullable
helpviewer_keywords:
- nullable compiler option [C#]
- /nullable compiler option [C#]
- -nullable compiler option [C#]
ms.openlocfilehash: f9c6c204d2563865f741c6ddb4644eb56f956c12
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125043"
---
# <a name="-nullable-c-compiler-options"></a><span data-ttu-id="6c968-103">-Nullable (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6c968-103">-nullable (C# Compiler Options)</span></span>

<span data-ttu-id="6c968-104">Možnost **-Nullable** umožňuje zadat požadovaný kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-104">The **-nullable** option lets you specify the desired nullable context.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c968-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c968-105">Syntax</span></span>

```console
-nullable[+ | -]
-nullable:{enable | disable | warnings | annotations}
```

## <a name="arguments"></a><span data-ttu-id="6c968-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6c968-106">Arguments</span></span>

<span data-ttu-id="6c968-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="6c968-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="6c968-108">Zadáním `+` nebo pouhou **možnou hodnotou null**způsobí, že kompilátor povolí kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-108">Specifying `+`, or just **-nullable**, causes the compiler to enable nullable context.</span></span> <span data-ttu-id="6c968-109">Určení `-` , které platí v případě, že neurčíte **hodnotu**null, zakážete kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-109">Specifying `-`, which is in effect if you do not specify **-nullable**, disables nullable context.</span></span>

<span data-ttu-id="6c968-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span><span class="sxs-lookup"><span data-stu-id="6c968-110">`enable` &#124; `disable` &#124; `warnings` &#124; `annotations`</span></span>  
<span data-ttu-id="6c968-111">Určuje možnost kontextu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-111">Specifies the nullable context option.</span></span> <span data-ttu-id="6c968-112">Podobně jako `+` nebo `-` , pokud chcete povolit a zakázat, ale umožňuje více členitosti kontextu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-112">Similar to `+` or `-`, to enable and disable, but allows for more granularity of nullable context specificity.</span></span> <span data-ttu-id="6c968-113">`enable`Argument, který je platný, jako Pokud zadáte **hodnotu null**, povoluje kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-113">The `enable` argument, which is in effect the same as if you specify **-nullable**, enables the nullable context.</span></span> <span data-ttu-id="6c968-114">Při zadání `disable` se zakáže kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-114">Specifying `disable` will disable nullable context.</span></span> <span data-ttu-id="6c968-115">Při zadání `warnings` argumentu **-Nullable:** Warnings je povolený kontext s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-115">When providing the `warnings` argument, **-nullable:warnings**, the nullable warning context is enabled.</span></span> <span data-ttu-id="6c968-116">Při zadávání `annotations` argumentu **-Nullable: Annotations**je povolený kontext anotace s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="6c968-116">When specifying the `annotations` argument, **-nullable:annotations**, the nullable annotation context is enabled.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c968-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c968-117">Remarks</span></span>

<span data-ttu-id="6c968-118">Analýza toku se používá k odvození hodnoty null proměnných v rámci spustitelného kódu.</span><span class="sxs-lookup"><span data-stu-id="6c968-118">Flow analysis is used to infer the nullability of variables within executable code.</span></span> <span data-ttu-id="6c968-119">Odvozená hodnota null proměnné je nezávislá na deklarované hodnotě null proměnné.</span><span class="sxs-lookup"><span data-stu-id="6c968-119">The inferred nullability of a variable is independent of the variable's declared nullability.</span></span> <span data-ttu-id="6c968-120">Volání metod jsou analyzována i v případě, že jsou podmíněně vynechána.</span><span class="sxs-lookup"><span data-stu-id="6c968-120">Method calls are analyzed even when they are conditionally omitted.</span></span> <span data-ttu-id="6c968-121">Například <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> v režimu vydání.</span><span class="sxs-lookup"><span data-stu-id="6c968-121">For instance, <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> in release mode.</span></span>

<span data-ttu-id="6c968-122">Vyvolání metod popsaných s následujícími atributy ovlivní také analýzu toků:</span><span class="sxs-lookup"><span data-stu-id="6c968-122">Invocation of methods annotated with the following attributes will also affect flow analysis:</span></span>

- <span data-ttu-id="6c968-123">Jednoduché předběžné podmínky: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> a <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span><span class="sxs-lookup"><span data-stu-id="6c968-123">Simple pre-conditions: <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute></span></span>
- <span data-ttu-id="6c968-124">Jednoduché následné stavy: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> a <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span><span class="sxs-lookup"><span data-stu-id="6c968-124">Simple post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullAttribute></span></span>
- <span data-ttu-id="6c968-125">Podmíněné následné podmínky: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> a <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span><span class="sxs-lookup"><span data-stu-id="6c968-125">Conditional post-conditions: <xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute> and <xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute></span></span>
- <span data-ttu-id="6c968-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (například `DoesNotReturnIf(false)` pro <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ) a <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span><span class="sxs-lookup"><span data-stu-id="6c968-126"><xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute> (for example, `DoesNotReturnIf(false)` for <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>) and <xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute></span></span>
- <xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute>
- <span data-ttu-id="6c968-127">Stavy po členu: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> a <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span><span class="sxs-lookup"><span data-stu-id="6c968-127">Member post-conditions: <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String)> and <xref:System.Diagnostics.CodeAnalysis.MemberNotNullAttribute.%23ctor(System.String[])></span></span>

### <a name="to-set-this-compiler-option-in-a-project"></a><span data-ttu-id="6c968-128">Nastavení této možnosti kompilátoru v projektu</span><span class="sxs-lookup"><span data-stu-id="6c968-128">To set this compiler option in a project</span></span>

<span data-ttu-id="6c968-129">Upravte soubor *. csproj* pro přidání `<Nullable>` značky v rámci `Project/PropertyGroup` hierarchie:</span><span class="sxs-lookup"><span data-stu-id="6c968-129">Edit the *.csproj* file to add the `<Nullable>` tag within a `Project/PropertyGroup` hierarchy:</span></span>

```xml
<Project Sdk="...">

  <PropertyGroup>
    <Nullable>enable</Nullable>
  </PropertyGroup>

</Project>
```

## <a name="see-also"></a><span data-ttu-id="6c968-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c968-130">See also</span></span>

- [<span data-ttu-id="6c968-131">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="6c968-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6c968-132">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="6c968-132">Nullable reference types</span></span>](../../nullable-references.md)
