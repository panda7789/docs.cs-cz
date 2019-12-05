---
title: -subsystemversion (C# možnosti kompilátoru)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802041"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="aa37d-102">-subsystemversion (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="aa37d-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="aa37d-103">Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit.</span><span class="sxs-lookup"><span data-stu-id="aa37d-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="aa37d-104">Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="aa37d-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="aa37d-105">Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](./target-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="aa37d-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa37d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa37d-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="aa37d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa37d-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="aa37d-108">Minimální požadovaná verze subsystému, jak je vyjádřena v zápisu tečky pro hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="aa37d-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="aa37d-109">Například můžete určit, že aplikace nemůže běžet v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6,01, jak je popsáno v tabulce dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="aa37d-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="aa37d-110">Je nutné zadat hodnoty pro `major` a `minor` jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="aa37d-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="aa37d-111">Počáteční nuly ve verzi `minor` nemění verzi, ale mají na konci nula.</span><span class="sxs-lookup"><span data-stu-id="aa37d-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="aa37d-112">Například 6,1 a 6,01 odkazují na stejnou verzi, ale 6,10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="aa37d-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="aa37d-113">Pokud chcete zabránit nejasnostem, doporučujeme, abyste podverze vyjádřili jako dvě číslice.</span><span class="sxs-lookup"><span data-stu-id="aa37d-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="aa37d-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa37d-114">Remarks</span></span>

<span data-ttu-id="aa37d-115">V následující tabulce jsou uvedeny běžné verze subsystému Windows.</span><span class="sxs-lookup"><span data-stu-id="aa37d-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="aa37d-116">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="aa37d-116">Windows version</span></span>|<span data-ttu-id="aa37d-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="aa37d-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="aa37d-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="aa37d-118">Windows 2000</span></span>|<span data-ttu-id="aa37d-119">5.00</span><span class="sxs-lookup"><span data-stu-id="aa37d-119">5.00</span></span>|
|<span data-ttu-id="aa37d-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="aa37d-120">Windows XP</span></span>|<span data-ttu-id="aa37d-121">5.01</span><span class="sxs-lookup"><span data-stu-id="aa37d-121">5.01</span></span>|
|<span data-ttu-id="aa37d-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="aa37d-122">Windows Server 2003</span></span>|<span data-ttu-id="aa37d-123">5.02</span><span class="sxs-lookup"><span data-stu-id="aa37d-123">5.02</span></span>|
|<span data-ttu-id="aa37d-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="aa37d-124">Windows Vista</span></span>|<span data-ttu-id="aa37d-125">6.00</span><span class="sxs-lookup"><span data-stu-id="aa37d-125">6.00</span></span>|
|<span data-ttu-id="aa37d-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="aa37d-126">Windows 7</span></span>|<span data-ttu-id="aa37d-127">6.01</span><span class="sxs-lookup"><span data-stu-id="aa37d-127">6.01</span></span>|
|<span data-ttu-id="aa37d-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="aa37d-128">Windows Server 2008</span></span>|<span data-ttu-id="aa37d-129">6.01</span><span class="sxs-lookup"><span data-stu-id="aa37d-129">6.01</span></span>|
|<span data-ttu-id="aa37d-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="aa37d-130">Windows 8</span></span>|<span data-ttu-id="aa37d-131">6.02</span><span class="sxs-lookup"><span data-stu-id="aa37d-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="aa37d-132">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="aa37d-132">Default values</span></span>

<span data-ttu-id="aa37d-133">Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="aa37d-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="aa37d-134">Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="aa37d-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="aa37d-135">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="aa37d-135">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="aa37d-136">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="aa37d-136">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="aa37d-137">-Platforma: ARM</span><span class="sxs-lookup"><span data-stu-id="aa37d-137">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="aa37d-138">Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="aa37d-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="aa37d-139">Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.</span><span class="sxs-lookup"><span data-stu-id="aa37d-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="aa37d-140">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="aa37d-140">Setting this option</span></span>

<span data-ttu-id="aa37d-141">Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. csproj a zadat hodnotu vlastnosti `SubsystemVersion` v souboru XML nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="aa37d-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="aa37d-142">Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa37d-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="aa37d-143">Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="aa37d-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa37d-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa37d-144">See also</span></span>

- [<span data-ttu-id="aa37d-145">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aa37d-145">C# Compiler Options</span></span>](./index.md)
