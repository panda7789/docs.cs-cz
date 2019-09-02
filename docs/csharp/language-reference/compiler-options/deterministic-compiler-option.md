---
title: -deterministické (C# možnosti kompilátoru)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e77c14a1c3a4ba11b8ae6556be4f1c3c0cd42788
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202917"
---
# <a name="-deterministic"></a><span data-ttu-id="4912c-102">-deterministic</span><span class="sxs-lookup"><span data-stu-id="4912c-102">-deterministic</span></span>

<span data-ttu-id="4912c-103">Způsobí, že kompilátor sestaví sestavení, jejichž výstup Byte-byte je stejný v rámci kompilací pro stejné vstupy.</span><span class="sxs-lookup"><span data-stu-id="4912c-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="4912c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4912c-104">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="4912c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4912c-105">Remarks</span></span>

<span data-ttu-id="4912c-106">Ve výchozím nastavení je výstup kompilátoru z dané sady vstupů jedinečný, protože kompilátor přidá časové razítko a identifikátor GUID, který je vygenerován z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="4912c-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="4912c-107">Použijete `-deterministic` možnost k vytvoření deterministického *sestavení*, jehož binární obsah je identický v rámci kompilací, pokud vstup zůstává stejný.</span><span class="sxs-lookup"><span data-stu-id="4912c-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="4912c-108">Kompilátor považuje za účel determinismem následující vstupy:</span><span class="sxs-lookup"><span data-stu-id="4912c-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="4912c-109">Sekvence parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4912c-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="4912c-110">Obsah souboru odpovědí kompilátoru. rsp</span><span class="sxs-lookup"><span data-stu-id="4912c-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="4912c-111">Byla použita přesná verze kompilátoru a jejich odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="4912c-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="4912c-112">Cesta k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="4912c-112">The current directory path.</span></span>
- <span data-ttu-id="4912c-113">Binární obsah všech souborů explicitně předaných kompilátoru buď přímo, nebo nepřímo, včetně:</span><span class="sxs-lookup"><span data-stu-id="4912c-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="4912c-114">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="4912c-114">Source files</span></span>
  - <span data-ttu-id="4912c-115">Odkazovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="4912c-115">Referenced assemblies</span></span>
  - <span data-ttu-id="4912c-116">Odkazované moduly</span><span class="sxs-lookup"><span data-stu-id="4912c-116">Referenced modules</span></span>
  - <span data-ttu-id="4912c-117">Prostředky</span><span class="sxs-lookup"><span data-stu-id="4912c-117">Resources</span></span>
  - <span data-ttu-id="4912c-118">Soubor klíče se silným názvem</span><span class="sxs-lookup"><span data-stu-id="4912c-118">The strong name key file</span></span>
  - <span data-ttu-id="4912c-119">soubory @ Response</span><span class="sxs-lookup"><span data-stu-id="4912c-119">@ response files</span></span>
  - <span data-ttu-id="4912c-120">Analyzátory</span><span class="sxs-lookup"><span data-stu-id="4912c-120">Analyzers</span></span>
  - <span data-ttu-id="4912c-121">Rulesets</span><span class="sxs-lookup"><span data-stu-id="4912c-121">Rulesets</span></span>
  - <span data-ttu-id="4912c-122">Další soubory, které mohou používat analyzátory</span><span class="sxs-lookup"><span data-stu-id="4912c-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="4912c-123">Aktuální jazyková verze (pro jazyk, ve kterém se vytvářejí zprávy o diagnostice a výjimkách).</span><span class="sxs-lookup"><span data-stu-id="4912c-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="4912c-124">Výchozí kódování (nebo aktuální znaková stránka), pokud kódování není zadáno.</span><span class="sxs-lookup"><span data-stu-id="4912c-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="4912c-125">Existence, neexistence a obsah souborů v cestách pro hledání kompilátoru (určené například pomocí `/lib` nebo `/recurse`).</span><span class="sxs-lookup"><span data-stu-id="4912c-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="4912c-126">Platforma CLR, na které je kompilátor spuštěn.</span><span class="sxs-lookup"><span data-stu-id="4912c-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="4912c-127">Hodnota `%LIBPATH%`, která může ovlivnit načítání závislostí analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="4912c-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="4912c-128">Pokud jsou zdroje veřejně dostupné, lze použít deterministické kompilace k určení, zda binární soubor je zkompilován z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="4912c-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="4912c-129">Může být také užitečné v souvislém systému sestavení pro určení, zda jsou kroky sestavení závislé na změnách binárních souborů nutné provést.</span><span class="sxs-lookup"><span data-stu-id="4912c-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4912c-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4912c-130">See also</span></span>

- [<span data-ttu-id="4912c-131">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4912c-131">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4912c-132">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4912c-132">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
