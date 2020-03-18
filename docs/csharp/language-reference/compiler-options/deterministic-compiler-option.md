---
title: -deterministický (Možnosti kompilátoru Jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: ed5d1db4618649391f88affad67e62dd9fc95925
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73455183"
---
# <a name="-deterministic"></a><span data-ttu-id="03a91-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="03a91-102">-deterministic</span></span>

<span data-ttu-id="03a91-103">Způsobí, že kompilátor k vytvoření sestavení, jehož bajt za bajt výstup je shodný napříč kompilace pro identické vstupy.</span><span class="sxs-lookup"><span data-stu-id="03a91-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="03a91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03a91-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="03a91-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03a91-105">Remarks</span></span>

<span data-ttu-id="03a91-106">Ve výchozím nastavení je výstup kompilátoru z dané sady vstupů jedinečný, protože kompilátor přidá časové razítko a identifikátor GUID generovaný z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="03a91-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="03a91-107">Tuto `-deterministic` možnost použijete k vytvoření *deterministického sestavení*, jehož binární obsah je napříč kompilacemi shodný, pokud vstup zůstane stejný.</span><span class="sxs-lookup"><span data-stu-id="03a91-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="03a91-108">Kompilátor považuje následující vstupy pro účely determinismu:</span><span class="sxs-lookup"><span data-stu-id="03a91-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="03a91-109">Posloupnost parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="03a91-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="03a91-110">Obsah souboru odpovědi RSP kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="03a91-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="03a91-111">Přesná verze použitého kompilátoru a jeho odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="03a91-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="03a91-112">Aktuální cesta k adresáři.</span><span class="sxs-lookup"><span data-stu-id="03a91-112">The current directory path.</span></span>
- <span data-ttu-id="03a91-113">Binární obsah všech souborů explicitně předán kompilátoru přímo nebo nepřímo, včetně:</span><span class="sxs-lookup"><span data-stu-id="03a91-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="03a91-114">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="03a91-114">Source files</span></span>
  - <span data-ttu-id="03a91-115">Odkazovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="03a91-115">Referenced assemblies</span></span>
  - <span data-ttu-id="03a91-116">Odkazované moduly</span><span class="sxs-lookup"><span data-stu-id="03a91-116">Referenced modules</span></span>
  - <span data-ttu-id="03a91-117">Zdroje informací</span><span class="sxs-lookup"><span data-stu-id="03a91-117">Resources</span></span>
  - <span data-ttu-id="03a91-118">Soubor klíče silného názvu</span><span class="sxs-lookup"><span data-stu-id="03a91-118">The strong name key file</span></span>
  - <span data-ttu-id="03a91-119">@ odpovědi soubory</span><span class="sxs-lookup"><span data-stu-id="03a91-119">@ response files</span></span>
  - <span data-ttu-id="03a91-120">Analyzátory</span><span class="sxs-lookup"><span data-stu-id="03a91-120">Analyzers</span></span>
  - <span data-ttu-id="03a91-121">Rulesets</span><span class="sxs-lookup"><span data-stu-id="03a91-121">Rulesets</span></span>
  - <span data-ttu-id="03a91-122">Další soubory, které mohou být použity analyzátory</span><span class="sxs-lookup"><span data-stu-id="03a91-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="03a91-123">Aktuální jazyková verze (pro jazyk, ve kterém jsou vytvářeny zprávy diagnostiky a výjimky).</span><span class="sxs-lookup"><span data-stu-id="03a91-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="03a91-124">Výchozí kódování (nebo aktuální znaková stránka), pokud kódování není zadáno.</span><span class="sxs-lookup"><span data-stu-id="03a91-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="03a91-125">Existence, neexistence a obsah souborů v cestách hledání kompilátoru (zadáno `-lib` například podle nebo `-recurse`).</span><span class="sxs-lookup"><span data-stu-id="03a91-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="03a91-126">Clr platformu, na kterém je spuštěn kompilátor.</span><span class="sxs-lookup"><span data-stu-id="03a91-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="03a91-127">Hodnota `%LIBPATH%`, která může ovlivnit načítání závislostí analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="03a91-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="03a91-128">Pokud jsou zdroje veřejně dostupné, deterministické kompilace lze použít pro určení, zda binární je kompilován z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="03a91-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="03a91-129">Může být také užitečné v systému průběžnésestavení pro určení, zda kroky sestavení, které jsou závislé na změny binární musí být provedeny.</span><span class="sxs-lookup"><span data-stu-id="03a91-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="03a91-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="03a91-130">See also</span></span>

- [<span data-ttu-id="03a91-131">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03a91-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="03a91-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="03a91-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
