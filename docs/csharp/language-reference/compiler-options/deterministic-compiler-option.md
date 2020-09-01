---
description: -deterministické (možnosti kompilátoru C#)
title: -deterministické (možnosti kompilátoru C#)
ms.date: 04/12/2018
f1_keywords:
- /deterministic
helpviewer_keywords:
- -deterministic compiler option [C#]
- deterministic compiler option [C#]
- /deterministic compiler option [C#]
ms.openlocfilehash: 9d0bcc2957e5a666c21cdc2ce61e74fc90fe3530
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125823"
---
# <a name="-deterministic"></a><span data-ttu-id="4b03c-103">-deterministic</span><span class="sxs-lookup"><span data-stu-id="4b03c-103">-deterministic</span></span>

<span data-ttu-id="4b03c-104">Způsobí, že kompilátor sestaví sestavení, jejichž výstup Byte-byte je stejný v rámci kompilací pro stejné vstupy.</span><span class="sxs-lookup"><span data-stu-id="4b03c-104">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b03c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b03c-105">Syntax</span></span>

```console
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="4b03c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b03c-106">Remarks</span></span>

<span data-ttu-id="4b03c-107">Ve výchozím nastavení je výstup kompilátoru z dané sady vstupů jedinečný, protože kompilátor přidá časové razítko a identifikátor GUID, který je vygenerován z náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="4b03c-107">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="4b03c-108">Použijete `-deterministic` možnost k vytvoření *deterministického sestavení*, jehož binární obsah je identický v rámci kompilací, pokud vstup zůstává stejný.</span><span class="sxs-lookup"><span data-stu-id="4b03c-108">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="4b03c-109">Kompilátor považuje za účel determinismem následující vstupy:</span><span class="sxs-lookup"><span data-stu-id="4b03c-109">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="4b03c-110">Sekvence parametrů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4b03c-110">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="4b03c-111">Obsah souboru odpovědí kompilátoru. rsp</span><span class="sxs-lookup"><span data-stu-id="4b03c-111">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="4b03c-112">Byla použita přesná verze kompilátoru a jejich odkazovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="4b03c-112">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="4b03c-113">Cesta k aktuálnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="4b03c-113">The current directory path.</span></span>
- <span data-ttu-id="4b03c-114">Binární obsah všech souborů explicitně předaných kompilátoru buď přímo, nebo nepřímo, včetně:</span><span class="sxs-lookup"><span data-stu-id="4b03c-114">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span>
  - <span data-ttu-id="4b03c-115">Zdrojové soubory</span><span class="sxs-lookup"><span data-stu-id="4b03c-115">Source files</span></span>
  - <span data-ttu-id="4b03c-116">Odkazovaná sestavení</span><span class="sxs-lookup"><span data-stu-id="4b03c-116">Referenced assemblies</span></span>
  - <span data-ttu-id="4b03c-117">Odkazované moduly</span><span class="sxs-lookup"><span data-stu-id="4b03c-117">Referenced modules</span></span>
  - <span data-ttu-id="4b03c-118">Zdroje a prostředky</span><span class="sxs-lookup"><span data-stu-id="4b03c-118">Resources</span></span>
  - <span data-ttu-id="4b03c-119">Soubor klíče se silným názvem</span><span class="sxs-lookup"><span data-stu-id="4b03c-119">The strong name key file</span></span>
  - <span data-ttu-id="4b03c-120">soubory @ Response</span><span class="sxs-lookup"><span data-stu-id="4b03c-120">@ response files</span></span>
  - <span data-ttu-id="4b03c-121">Analyzátory</span><span class="sxs-lookup"><span data-stu-id="4b03c-121">Analyzers</span></span>
  - <span data-ttu-id="4b03c-122">Rulesets</span><span class="sxs-lookup"><span data-stu-id="4b03c-122">Rulesets</span></span>
  - <span data-ttu-id="4b03c-123">Další soubory, které mohou používat analyzátory</span><span class="sxs-lookup"><span data-stu-id="4b03c-123">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="4b03c-124">Aktuální jazyková verze (pro jazyk, ve kterém se vytvářejí zprávy o diagnostice a výjimkách).</span><span class="sxs-lookup"><span data-stu-id="4b03c-124">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="4b03c-125">Výchozí kódování (nebo aktuální znaková stránka), pokud kódování není zadáno.</span><span class="sxs-lookup"><span data-stu-id="4b03c-125">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="4b03c-126">Existence, neexistence a obsah souborů v cestách pro hledání kompilátoru (určené například pomocí `-lib` nebo `-recurse` ).</span><span class="sxs-lookup"><span data-stu-id="4b03c-126">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `-lib` or `-recurse`).</span></span>
- <span data-ttu-id="4b03c-127">Platforma CLR, na které je kompilátor spuštěn.</span><span class="sxs-lookup"><span data-stu-id="4b03c-127">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="4b03c-128">Hodnota `%LIBPATH%` , která může ovlivnit načítání závislostí analyzátoru.</span><span class="sxs-lookup"><span data-stu-id="4b03c-128">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="4b03c-129">Pokud jsou zdroje veřejně dostupné, lze použít deterministické kompilace k určení, zda binární soubor je zkompilován z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="4b03c-129">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="4b03c-130">Může být také užitečné v souvislém systému sestavení pro určení, zda jsou kroky sestavení závislé na změnách binárních souborů nutné provést.</span><span class="sxs-lookup"><span data-stu-id="4b03c-130">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b03c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b03c-131">See also</span></span>

- [<span data-ttu-id="4b03c-132">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="4b03c-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4b03c-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="4b03c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
