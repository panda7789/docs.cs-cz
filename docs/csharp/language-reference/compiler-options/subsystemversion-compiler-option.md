---
description: -subsystemversion (možnosti kompilátoru C#)
title: -subsystemversion (možnosti kompilátoru C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: e8001d8db214123e75fec4e1d1117ef90a9df606
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128592"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="1a60e-103">-subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1a60e-103">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="1a60e-104">Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit.</span><span class="sxs-lookup"><span data-stu-id="1a60e-104">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="1a60e-105">Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="1a60e-105">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="1a60e-106">Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](./target-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="1a60e-106">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a60e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a60e-107">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="1a60e-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a60e-108">Parameters</span></span>

`major.minor`

<span data-ttu-id="1a60e-109">Minimální požadovaná verze subsystému, jak je vyjádřena v zápisu tečky pro hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="1a60e-109">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="1a60e-110">Například můžete určit, že aplikace nemůže běžet v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6,01, jak je popsáno v tabulce dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="1a60e-110">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="1a60e-111">Je nutné zadat hodnoty pro `major` a `minor` jako celé číslo.</span><span class="sxs-lookup"><span data-stu-id="1a60e-111">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="1a60e-112">Počáteční nuly ve `minor` verzi nemění verzi, ale mají na konci nula.</span><span class="sxs-lookup"><span data-stu-id="1a60e-112">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="1a60e-113">Například 6,1 a 6,01 odkazují na stejnou verzi, ale 6,10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="1a60e-113">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="1a60e-114">Pokud chcete zabránit nejasnostem, doporučujeme, abyste podverze vyjádřili jako dvě číslice.</span><span class="sxs-lookup"><span data-stu-id="1a60e-114">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a60e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a60e-115">Remarks</span></span>

<span data-ttu-id="1a60e-116">V následující tabulce jsou uvedeny běžné verze subsystému Windows.</span><span class="sxs-lookup"><span data-stu-id="1a60e-116">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="1a60e-117">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="1a60e-117">Windows version</span></span>|<span data-ttu-id="1a60e-118">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="1a60e-118">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="1a60e-119">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="1a60e-119">Windows 2000</span></span>|<span data-ttu-id="1a60e-120">5,00</span><span class="sxs-lookup"><span data-stu-id="1a60e-120">5.00</span></span>|
|<span data-ttu-id="1a60e-121">Windows XP</span><span class="sxs-lookup"><span data-stu-id="1a60e-121">Windows XP</span></span>|<span data-ttu-id="1a60e-122">5,01</span><span class="sxs-lookup"><span data-stu-id="1a60e-122">5.01</span></span>|
|<span data-ttu-id="1a60e-123">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="1a60e-123">Windows Server 2003</span></span>|<span data-ttu-id="1a60e-124">5,02</span><span class="sxs-lookup"><span data-stu-id="1a60e-124">5.02</span></span>|
|<span data-ttu-id="1a60e-125">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="1a60e-125">Windows Vista</span></span>|<span data-ttu-id="1a60e-126">6,00</span><span class="sxs-lookup"><span data-stu-id="1a60e-126">6.00</span></span>|
|<span data-ttu-id="1a60e-127">Windows 7</span><span class="sxs-lookup"><span data-stu-id="1a60e-127">Windows 7</span></span>|<span data-ttu-id="1a60e-128">6,01</span><span class="sxs-lookup"><span data-stu-id="1a60e-128">6.01</span></span>|
|<span data-ttu-id="1a60e-129">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="1a60e-129">Windows Server 2008</span></span>|<span data-ttu-id="1a60e-130">6,01</span><span class="sxs-lookup"><span data-stu-id="1a60e-130">6.01</span></span>|
|<span data-ttu-id="1a60e-131">Windows 8</span><span class="sxs-lookup"><span data-stu-id="1a60e-131">Windows 8</span></span>|<span data-ttu-id="1a60e-132">6,02</span><span class="sxs-lookup"><span data-stu-id="1a60e-132">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="1a60e-133">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="1a60e-133">Default values</span></span>

<span data-ttu-id="1a60e-134">Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="1a60e-134">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="1a60e-135">Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="1a60e-135">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="1a60e-136">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="1a60e-136">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="1a60e-137">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="1a60e-137">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="1a60e-138">-Platforma: ARM</span><span class="sxs-lookup"><span data-stu-id="1a60e-138">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="1a60e-139">Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="1a60e-139">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="1a60e-140">Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.</span><span class="sxs-lookup"><span data-stu-id="1a60e-140">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="1a60e-141">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="1a60e-141">Setting this option</span></span>

<span data-ttu-id="1a60e-142">Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. csproj a zadat hodnotu `SubsystemVersion` vlastnosti v souboru XML nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1a60e-142">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="1a60e-143">Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a60e-143">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="1a60e-144">Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="1a60e-144">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a60e-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a60e-145">See also</span></span>

- [<span data-ttu-id="1a60e-146">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="1a60e-146">C# Compiler Options</span></span>](./index.md)
