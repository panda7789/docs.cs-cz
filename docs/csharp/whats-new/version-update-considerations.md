---
title: Požadavky na verzi a aktualizace pro vývojáře v jazyce C#
description: Zavedení nových funkcí jazyků do knihovny může mít vliv na kód, který ho používá.
ms.topic: reference
ms.date: 09/19/2018
ms.openlocfilehash: f7db7c79792d04bcf592bc1858e1f0f05cb34402
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88268124"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="b1088-103">Požadavky na verzi a aktualizace pro vývojáře v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b1088-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="b1088-104">Kompatibilita je velice důležitým cílem při přidávání nových funkcí do jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="b1088-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="b1088-105">Ve většině případů může být existující kód znovu zkompilován s novou verzí kompilátoru bez jakýchkoli potíží.</span><span class="sxs-lookup"><span data-stu-id="b1088-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="b1088-106">Při přijímání nových funkcí jazyka v knihovně se může vyžadovat lepší péče.</span><span class="sxs-lookup"><span data-stu-id="b1088-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="b1088-107">Je možné, že vytváříte novou knihovnu s funkcemi nalezenými v nejnovější verzi a potřebujete zajistit, aby aplikace sestavené pomocí předchozích verzí kompilátoru mohla použít.</span><span class="sxs-lookup"><span data-stu-id="b1088-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="b1088-108">Nebo můžete upgradovat existující knihovnu a mnoho uživatelů možná ještě neupgradoval verze.</span><span class="sxs-lookup"><span data-stu-id="b1088-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="b1088-109">Při rozhodování o přijímání nových funkcí je potřeba vzít v úvahu dvě varianty kompatibility: kompatibilní se zdrojem a binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b1088-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="b1088-110">Binární kompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="b1088-110">Binary compatible changes</span></span>

<span data-ttu-id="b1088-111">Změny v knihovně jsou **binární, kompatibilní** s tím, že aktualizovaná knihovna může být použita bez nutnosti znovu sestavovat aplikace a knihovny, které ji používají.</span><span class="sxs-lookup"><span data-stu-id="b1088-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="b1088-112">Závislá sestavení není nutné znovu sestavit, ani nejsou vyžadovány žádné změny zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="b1088-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="b1088-113">Změny binární kompatibility jsou také kompatibilní se zdroji.</span><span class="sxs-lookup"><span data-stu-id="b1088-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="b1088-114">Změny kompatibilní se zdrojem</span><span class="sxs-lookup"><span data-stu-id="b1088-114">Source compatible changes</span></span>

<span data-ttu-id="b1088-115">Změny v knihovně jsou **kompatibilní se zdrojem** , když aplikace a knihovny, které používají vaši knihovnu, nevyžadují změny zdrojového kódu, ale zdroj musí být znovu zkompilován z důvodu správné správné správné verze.</span><span class="sxs-lookup"><span data-stu-id="b1088-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="b1088-116">Nekompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="b1088-116">Incompatible changes</span></span>

<span data-ttu-id="b1088-117">Pokud změna není kompatibilní se **zdrojem** ani v **binárním**formátu, jsou v závislých knihovnách a aplikacích vyžadovány změny zdrojového kódu společně s opětovnou kompilací.</span><span class="sxs-lookup"><span data-stu-id="b1088-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="b1088-118">Vyhodnocení knihovny</span><span class="sxs-lookup"><span data-stu-id="b1088-118">Evaluate your library</span></span>

<span data-ttu-id="b1088-119">Tyto koncepce kompatibility mají vliv na veřejné a chráněné deklarace pro vaši knihovnu, nikoli na její interní implementaci.</span><span class="sxs-lookup"><span data-stu-id="b1088-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="b1088-120">Interní přijímání nových funkcí je v **binárním**formátu vždycky kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b1088-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="b1088-121">**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný zkompilovaný kód pro veřejné deklarace jako starší syntaxi.</span><span class="sxs-lookup"><span data-stu-id="b1088-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="b1088-122">Například změna metody na člena Expression-těle je **binární kompatibilní** změna:</span><span class="sxs-lookup"><span data-stu-id="b1088-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="b1088-123">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="b1088-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="b1088-124">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="b1088-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="b1088-125">Změny **kompatibilní se zdrojem** zavádí syntaxi, která mění zkompilovaný kód pro veřejný člen, ale způsobem, který je kompatibilní s existujícími lokalitami volání.</span><span class="sxs-lookup"><span data-stu-id="b1088-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="b1088-126">Například změna signatury metody z parametru podle hodnoty na `in` parametr podle odkazu je kompatibilní se zdrojem, ale není kompatibilní s binárním:</span><span class="sxs-lookup"><span data-stu-id="b1088-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="b1088-127">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="b1088-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="b1088-128">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="b1088-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="b1088-129">Poznámky k [novinkám](index.md) , pokud zavádíte funkci, která má vliv na veřejné deklarace, jsou kompatibilní se zdrojem nebo binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="b1088-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>
