---
title: Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#
description: Zavedení nových funkcí jazyků v knihovně může mít vliv na kód, který ji používá.
ms.date: 09/19/2018
ms.openlocfilehash: 3ffe2f6fd64a391fddf28233dccb022c95851884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399383"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="29edf-103">Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#</span><span class="sxs-lookup"><span data-stu-id="29edf-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="29edf-104">Kompatibilita je velmi důležitý cíl jako nové funkce jsou přidány do jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="29edf-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="29edf-105">Téměř ve všech případech lze existující kód znovu zkompilovat s novou verzí kompilátoru bez problémů.</span><span class="sxs-lookup"><span data-stu-id="29edf-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="29edf-106">Při zavádění nových jazykových funkcí v knihovně může být vyžadována větší péče.</span><span class="sxs-lookup"><span data-stu-id="29edf-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="29edf-107">Možná vytváříte novou knihovnu s funkcemi, které se nacházejí v nejnovější verzi, a potřebujete zajistit, aby aplikace vytvořené pomocí předchozích verzí kompilátoru mohly používat.</span><span class="sxs-lookup"><span data-stu-id="29edf-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="29edf-108">Nebo je možné, že upgradujete existující knihovnu a mnoho uživatelů ještě nemá inovované verze.</span><span class="sxs-lookup"><span data-stu-id="29edf-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="29edf-109">Při rozhodování o přijetí nových funkcí budete muset zvážit dvě varianty kompatibility: kompatibilitu se zdrojem a binární kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="29edf-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="29edf-110">Binární kompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="29edf-110">Binary compatible changes</span></span>

<span data-ttu-id="29edf-111">Změny v knihovně jsou **binární kompatibilní,** pokud lze aktualizovanou knihovnu použít bez opětovného sestavení aplikací a knihoven, které ji používají.</span><span class="sxs-lookup"><span data-stu-id="29edf-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="29edf-112">Závislé sestavení není nutné znovu sestavit, ani nejsou vyžadovány žádné změny zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="29edf-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="29edf-113">Binární kompatibilní změny jsou také změny kompatibilní se zdrojem.</span><span class="sxs-lookup"><span data-stu-id="29edf-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="29edf-114">Změny kompatibilní se zdrojem</span><span class="sxs-lookup"><span data-stu-id="29edf-114">Source compatible changes</span></span>

<span data-ttu-id="29edf-115">Změny v knihovně jsou **kompatibilní se zdrojem,** pokud aplikace a knihovny, které používají vaši knihovnu, nevyžadují změny zdrojového kódu, ale zdroj musí být znovu zkompilován proti nové verzi, aby fungoval správně.</span><span class="sxs-lookup"><span data-stu-id="29edf-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="29edf-116">Nekompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="29edf-116">Incompatible changes</span></span>

<span data-ttu-id="29edf-117">Pokud změna není ani **zdrojkompatibilní,** ani **binární kompatibilní**, změny zdrojového kódu spolu s rekompilace jsou vyžadovány v závislých knihovnách a aplikacích.</span><span class="sxs-lookup"><span data-stu-id="29edf-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="29edf-118">Vyhodnocení knihovny</span><span class="sxs-lookup"><span data-stu-id="29edf-118">Evaluate your library</span></span>

<span data-ttu-id="29edf-119">Tyto koncepty kompatibility ovlivňují veřejné a chráněné deklarace pro vaši knihovnu, nikoli její interní implementaci.</span><span class="sxs-lookup"><span data-stu-id="29edf-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="29edf-120">Přijetí všech nových funkcí interně jsou vždy **binární kompatibilní**.</span><span class="sxs-lookup"><span data-stu-id="29edf-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="29edf-121">**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný kompilovaný kód pro veřejná prohlášení jako starší syntaxe.</span><span class="sxs-lookup"><span data-stu-id="29edf-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="29edf-122">Například změna metody na člen s výrazem je **binární kompatibilní** změna:</span><span class="sxs-lookup"><span data-stu-id="29edf-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="29edf-123">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="29edf-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="29edf-124">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="29edf-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="29edf-125">**Změny kompatibilní se zdrojem** zavádějí syntaxi, která mění zkompilovaný kód pro veřejného člena, ale způsobem, který je kompatibilní s existujícími weby volání.</span><span class="sxs-lookup"><span data-stu-id="29edf-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="29edf-126">Například změna podpisu metody z parametru `in` podle hodnoty na parametr podle odkazu je kompatibilní se zdrojem, ale není kompatibilní s binárním souborem:</span><span class="sxs-lookup"><span data-stu-id="29edf-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="29edf-127">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="29edf-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="29edf-128">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="29edf-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="29edf-129">[Co je nového](index.md) články na vědomí, pokud zavedení funkce, která ovlivňuje veřejné deklarace je zdroj kompatibilní nebo binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="29edf-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
