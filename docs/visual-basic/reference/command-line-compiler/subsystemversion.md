---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: e8607f8254783b5486b02ccc4c7e4081da506fae
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802160"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="6e804-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e804-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="6e804-103">Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit.</span><span class="sxs-lookup"><span data-stu-id="6e804-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="6e804-104">Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="6e804-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="6e804-105">Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="6e804-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e804-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e804-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="6e804-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e804-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="6e804-108">Minimální požadovaná verze subsystému, jak je vyjádřena v zápisu tečky pro hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="6e804-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="6e804-109">Například můžete určit, že aplikace nemůže běžet v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6,01, jak je popsáno v tabulce dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="6e804-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="6e804-110">Je nutné zadat hodnoty pro `major` a `minor` jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="6e804-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="6e804-111">Počáteční nuly ve verzi `minor` nemění verzi, ale mají na konci nula.</span><span class="sxs-lookup"><span data-stu-id="6e804-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="6e804-112">Například 6,1 a 6,01 odkazují na stejnou verzi, ale 6,10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="6e804-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="6e804-113">Pokud chcete zabránit nejasnostem, doporučujeme, abyste podverze vyjádřili jako dvě číslice.</span><span class="sxs-lookup"><span data-stu-id="6e804-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="6e804-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e804-114">Remarks</span></span>

<span data-ttu-id="6e804-115">V následující tabulce jsou uvedeny běžné verze subsystému Windows.</span><span class="sxs-lookup"><span data-stu-id="6e804-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="6e804-116">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="6e804-116">Windows version</span></span>|<span data-ttu-id="6e804-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="6e804-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="6e804-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="6e804-118">Windows 2000</span></span>|<span data-ttu-id="6e804-119">5.00</span><span class="sxs-lookup"><span data-stu-id="6e804-119">5.00</span></span>|
|<span data-ttu-id="6e804-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="6e804-120">Windows XP</span></span>|<span data-ttu-id="6e804-121">5.01</span><span class="sxs-lookup"><span data-stu-id="6e804-121">5.01</span></span>|
|<span data-ttu-id="6e804-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="6e804-122">Windows Server 2003</span></span>|<span data-ttu-id="6e804-123">5.02</span><span class="sxs-lookup"><span data-stu-id="6e804-123">5.02</span></span>|
|<span data-ttu-id="6e804-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="6e804-124">Windows Vista</span></span>|<span data-ttu-id="6e804-125">6.00</span><span class="sxs-lookup"><span data-stu-id="6e804-125">6.00</span></span>|
|<span data-ttu-id="6e804-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="6e804-126">Windows 7</span></span>|<span data-ttu-id="6e804-127">6.01</span><span class="sxs-lookup"><span data-stu-id="6e804-127">6.01</span></span>|
|<span data-ttu-id="6e804-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="6e804-128">Windows Server 2008</span></span>|<span data-ttu-id="6e804-129">6.01</span><span class="sxs-lookup"><span data-stu-id="6e804-129">6.01</span></span>|
|<span data-ttu-id="6e804-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="6e804-130">Windows 8</span></span>|<span data-ttu-id="6e804-131">6.02</span><span class="sxs-lookup"><span data-stu-id="6e804-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="6e804-132">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="6e804-132">Default values</span></span>

<span data-ttu-id="6e804-133">Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="6e804-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="6e804-134">Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="6e804-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="6e804-135">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="6e804-135">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="6e804-136">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="6e804-136">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="6e804-137">-Platforma: ARM</span><span class="sxs-lookup"><span data-stu-id="6e804-137">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)

- <span data-ttu-id="6e804-138">Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="6e804-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="6e804-139">Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.</span><span class="sxs-lookup"><span data-stu-id="6e804-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="6e804-140">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="6e804-140">Setting this option</span></span>

<span data-ttu-id="6e804-141">Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. vbproj a zadat hodnotu vlastnosti `SubsystemVersion` v souboru XML nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6e804-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="6e804-142">Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e804-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="6e804-143">Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="6e804-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e804-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e804-144">See also</span></span>

- [<span data-ttu-id="6e804-145">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="6e804-145">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

- [<span data-ttu-id="6e804-146">Vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="6e804-146">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
