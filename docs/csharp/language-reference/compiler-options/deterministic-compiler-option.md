---
title: -deterministické (možnosti kompilátoru C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 819e0c44d933b491091c05d1c28b30827ead85ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499843"
---
# <a name="-deterministic"></a><span data-ttu-id="5d6fe-102">-deterministické</span><span class="sxs-lookup"><span data-stu-id="5d6fe-102">-deterministic</span></span>

<span data-ttu-id="5d6fe-103">Způsobí, že kompilátor vytvoří sestavení, jehož výstup bajt po bajtu je identické napříč kompilace identické vstupů.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="5d6fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d6fe-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="5d6fe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d6fe-105">Remarks</span></span>

<span data-ttu-id="5d6fe-106">Ve výchozím nastavení je výstup kompilátoru z danou sadu vstupů jedinečná, vzhledem k tomu, že kompilátor přidává časové razítko a identifikátor GUID, který je generován z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="5d6fe-107">Můžete použít `-deterministic` možnost vytvářet *deterministické sestavení*, jehož binární obsah identické napříč kompilace jako vstup zůstává stejná.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="5d6fe-108">Kompilátor bere v úvahu následující vstupy pro účely determinismus:</span><span class="sxs-lookup"><span data-stu-id="5d6fe-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="5d6fe-109">Pořadí parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="5d6fe-110">Obsah souboru odezvy kompilátoru .rsp.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="5d6fe-111">Přesné verze kompilátoru použít a jeho odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="5d6fe-112">Aktuální cesta k adresáři.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-112">The current directory path.</span></span>
- <span data-ttu-id="5d6fe-113">Binární obsah všech souborů explicitně předány kompilátoru přímo nebo nepřímo, včetně:</span><span class="sxs-lookup"><span data-stu-id="5d6fe-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
    - <span data-ttu-id="5d6fe-114">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="5d6fe-114">Source files</span></span>
    - <span data-ttu-id="5d6fe-115">Odkazovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="5d6fe-115">Referenced assemblies</span></span>
    - <span data-ttu-id="5d6fe-116">Odkazované moduly</span><span class="sxs-lookup"><span data-stu-id="5d6fe-116">Referenced modules</span></span>
    - <span data-ttu-id="5d6fe-117">Prostředky</span><span class="sxs-lookup"><span data-stu-id="5d6fe-117">Resources</span></span>
    - <span data-ttu-id="5d6fe-118">Soubor klíče se silným názvem</span><span class="sxs-lookup"><span data-stu-id="5d6fe-118">The strong name key file</span></span>
    - <span data-ttu-id="5d6fe-119">@ soubory odpovědí</span><span class="sxs-lookup"><span data-stu-id="5d6fe-119">@ response files</span></span>
    - <span data-ttu-id="5d6fe-120">Analyzátory</span><span class="sxs-lookup"><span data-stu-id="5d6fe-120">Analyzers</span></span>
    - <span data-ttu-id="5d6fe-121">Sady pravidel</span><span class="sxs-lookup"><span data-stu-id="5d6fe-121">Rulesets</span></span>
    - <span data-ttu-id="5d6fe-122">Další soubory, které mohou být využívána analyzátory</span><span class="sxs-lookup"><span data-stu-id="5d6fe-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="5d6fe-123">Aktuální jazykové verze (pro jazyk, v které diagnostiky a výjimky se budou vytvářet zprávy).</span><span class="sxs-lookup"><span data-stu-id="5d6fe-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="5d6fe-124">Výchozí kódování (nebo aktuální znakové stránce) Pokud kódování není zadán.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="5d6fe-125">Existence, neexistence a obsah souborů na vyhledávací cesty kompilátoru (například tím, že zadaný `/lib` nebo `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="5d6fe-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="5d6fe-126">Platforma CLR, na kterém je spuštěna kompilátor.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="5d6fe-127">Hodnota `%LIBPATH%`, což může ovlivnit načítání analyzátoru závislostí.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="5d6fe-128">Když jsou veřejně dostupné zdroje, deterministickou kompilaci lze použít pro stanovení, zda je zkompilován do binárního souboru z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="5d6fe-129">Může být také užitečné v systému průběžného sestavení pro určení, jestli je potřeba spustit kroky sestavení, které jsou závislé na změny do binárního souboru.</span><span class="sxs-lookup"><span data-stu-id="5d6fe-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="5d6fe-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d6fe-130">See also</span></span>

- [<span data-ttu-id="5d6fe-131">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5d6fe-131">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="5d6fe-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="5d6fe-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
