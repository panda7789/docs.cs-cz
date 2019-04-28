---
title: Verze a aktualizace důležité informace pro vývojáře v C#
description: Představení nových funkcí jazyků v knihovně může mít vliv na kód, který ji používá.
ms.date: 09/19/2018
ms.openlocfilehash: 56685422e2c73dcca25acbdccb3a77a8de9df775
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675504"
---
# <a name="version-and-update-considerations-for-c-developers"></a><span data-ttu-id="013d4-103">Verze a aktualizace důležité informace pro vývojáře v C#</span><span class="sxs-lookup"><span data-stu-id="013d4-103">Version and update considerations for C# developers</span></span>

<span data-ttu-id="013d4-104">Kompatibilita je velmi důležité cílem přidávání nových funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="013d4-104">Compatibility is a very important goal as new features are added to the C# language.</span></span> <span data-ttu-id="013d4-105">V téměř všech případech se můžete znovu zkompilovat existujícího kódu pomocí nové verze kompilátoru bez jakýkoli problém.</span><span class="sxs-lookup"><span data-stu-id="013d4-105">In almost all cases, existing code can be recompiled with a new compiler version without any issue.</span></span>

<span data-ttu-id="013d4-106">Větší péči se může vyžadovat při přijetí nové funkce jazyků v knihovně.</span><span class="sxs-lookup"><span data-stu-id="013d4-106">More care may be required when you adopt new language features in a library.</span></span> <span data-ttu-id="013d4-107">Může vytvářet nové knihovny s funkcemi, které jsou k dispozici v nejnovější verzi a potřebujete zajistit aplikací vytvořených pomocí předchozí verze kompilátoru ji použít.</span><span class="sxs-lookup"><span data-stu-id="013d4-107">You may be creating a new library with features found in the latest version and need to ensure apps built using previous versions of the compiler can use it.</span></span> <span data-ttu-id="013d4-108">Nebo upgradu existující knihovnu a mnoho z vašich uživatelů nemusí upgradu verze ještě.</span><span class="sxs-lookup"><span data-stu-id="013d4-108">Or you may be upgrading an existing library and many of your users may not have upgraded versions yet.</span></span> <span data-ttu-id="013d4-109">Při provádění rozhodnutí o zavedení nových funkcí, je potřeba vzít v úvahu dvě varianty kompatibility: zdroj kompatibilní a binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="013d4-109">As you make decisions on adopting new features, you'll need to consider two variations of compatibility: source compatible and binary compatible.</span></span>

## <a name="binary-compatible-changes"></a><span data-ttu-id="013d4-110">Binární kompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="013d4-110">Binary compatible changes</span></span>

<span data-ttu-id="013d4-111">Změny knihovny jsou **binární kompatibilní** při aktualizované knihovny je možné bez nutnosti opětovného sestavení aplikací a knihoven, které ji používají.</span><span class="sxs-lookup"><span data-stu-id="013d4-111">Changes to your library are **binary compatible** when your updated library can be used without rebuilding applications and libraries that use it.</span></span> <span data-ttu-id="013d4-112">Závislá sestavení nejsou nutné znovu sestavit ani jsou nutné změny zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="013d4-112">Dependent assemblies are not required to be rebuilt, nor are any source code changes required.</span></span> <span data-ttu-id="013d4-113">Binární kompatibilní změny jsou i změny kompatibilní zdroj.</span><span class="sxs-lookup"><span data-stu-id="013d4-113">Binary compatible changes are also source compatible changes.</span></span>

## <a name="source-compatible-changes"></a><span data-ttu-id="013d4-114">Kompatibilní změny zdroje</span><span class="sxs-lookup"><span data-stu-id="013d4-114">Source compatible changes</span></span>

<span data-ttu-id="013d4-115">Změny knihovny jsou **zdroj kompatibilní** při aplikací a knihoven, které používají knihovnu nevyžadují změny zdrojového kódu, ale zdroj musí zopakovat na novou verzi fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="013d4-115">Changes to your library are **source compatible** when applications and libraries that use your library do not require source code changes, but the source must be recompiled against the new version to work correctly.</span></span>

## <a name="incompatible-changes"></a><span data-ttu-id="013d4-116">Nekompatibilní změny</span><span class="sxs-lookup"><span data-stu-id="013d4-116">Incompatible changes</span></span>

<span data-ttu-id="013d4-117">Pokud změna není ani **zdroj kompatibilní** ani **binární kompatibilní**, jsou nezbytné změny zdrojového kódu společně s rekompilace závislé knihovny a aplikace.</span><span class="sxs-lookup"><span data-stu-id="013d4-117">If a change is neither **source compatible** nor **binary compatible**, source code changes along with recompilation are required in dependent libraries and applications.</span></span>

## <a name="evaluate-your-library"></a><span data-ttu-id="013d4-118">Vyhodnocení knihovny</span><span class="sxs-lookup"><span data-stu-id="013d4-118">Evaluate your library</span></span>

<span data-ttu-id="013d4-119">Tyto koncepty kompatibility vliv na deklarace veřejné a chráněné knihovny, nikoli jeho vnitřní implementace.</span><span class="sxs-lookup"><span data-stu-id="013d4-119">These compatibility concepts affect the public and protected declarations for your library, not its internal implementation.</span></span> <span data-ttu-id="013d4-120">Interně přijímat žádné nové funkce jsou vždy **binární kompatibilní**.</span><span class="sxs-lookup"><span data-stu-id="013d4-120">Adopting any new features internally are always **binary compatible**.</span></span>  

<span data-ttu-id="013d4-121">**Binární kompatibilní** změny poskytují novou syntaxi, která generuje stejný zkompilovaný kód pro veřejné deklarace jako starší syntaxe.</span><span class="sxs-lookup"><span data-stu-id="013d4-121">**Binary compatible** changes provide new syntax that generates the same compiled code for public declarations as the older syntax.</span></span> <span data-ttu-id="013d4-122">Například změna metody pro člena s výrazem v těle je **binární kompatibilní** změnit:</span><span class="sxs-lookup"><span data-stu-id="013d4-122">For example, changing a method to an expression-bodied member is a **binary compatible** change:</span></span>

<span data-ttu-id="013d4-123">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="013d4-123">Original code:</span></span>

```csharp
public double CalculateSquare(double value)
{
    return value * value;
}
```

<span data-ttu-id="013d4-124">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="013d4-124">New code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="013d4-125">**Zdroj kompatibilní** změny zavedou syntaxe, která se mění zkompilovaný kód pro veřejný člen, ale v způsobem, který je kompatibilní s existující lokalit volání.</span><span class="sxs-lookup"><span data-stu-id="013d4-125">**Source compatible** changes introduce syntax that changes the compiled code for a public member, but in a way that is compatible with existing call sites.</span></span> <span data-ttu-id="013d4-126">Například změna podpisu metody z parametrem hodnotu do `in` odkazem. parametr je zdroj kompatibilní, ale nikoli binární kompatibilní:</span><span class="sxs-lookup"><span data-stu-id="013d4-126">For example, changing a method signature from a by value parameter to an `in` by reference parameter is source compatible, but not binary compatible:</span></span>

<span data-ttu-id="013d4-127">Původní kód:</span><span class="sxs-lookup"><span data-stu-id="013d4-127">Original code:</span></span>

```csharp
public double CalculateSquare(double value) => value * value;
```

<span data-ttu-id="013d4-128">Nový kód:</span><span class="sxs-lookup"><span data-stu-id="013d4-128">New code:</span></span>

```csharp
public double CalculateSquare(in double value) => value * value;
```

<span data-ttu-id="013d4-129">[Novinky](index.md) články Poznámka: Pokud představení funkce, která má vliv na veřejné deklarace kompatibilní zdroj nebo binární kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="013d4-129">The [What's new](index.md) articles note if introducing a feature that affects public declarations is source compatible or binary compatible.</span></span>