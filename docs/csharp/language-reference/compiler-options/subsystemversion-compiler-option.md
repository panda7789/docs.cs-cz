---
title: -subsystemversion (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802041"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="994c4-102">-subsystemversion (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="994c4-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="994c4-103">Určuje minimální verzi subsystému, ve kterém může být spuštěn generovaný spustitelný soubor, čímž určí verze systému Windows, ve kterých lze spustit spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="994c4-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="994c4-104">Tato možnost nejčastěji zajišťuje, že spustitelný soubor může využívat určité funkce zabezpečení, které nejsou k dispozici ve starších verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="994c4-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="994c4-105">Chcete-li určit samotný subsystém, použijte možnost kompilátoru [-target.](./target-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="994c4-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="994c4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="994c4-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="994c4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="994c4-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="994c4-108">Minimální požadovaná verze subsystému vyjádřená v zápisu dot pro hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="994c4-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="994c4-109">Můžete například určit, že aplikace nemůže být spuštěna v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6.01, jak popisuje tabulka dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="994c4-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="994c4-110">Je nutné zadat `major` hodnoty `minor` pro a jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="994c4-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="994c4-111">Úvodní nuly `minor` ve verzi nemění verzi, ale koncové nuly ano.</span><span class="sxs-lookup"><span data-stu-id="994c4-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="994c4-112">Například 6.1 a 6.01 odkazují na stejnou verzi, ale 6.10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="994c4-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="994c4-113">Doporučujeme vyjádřit dílčí verzi jako dvě číslice, aby nedošlo k záměně.</span><span class="sxs-lookup"><span data-stu-id="994c4-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="994c4-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="994c4-114">Remarks</span></span>

<span data-ttu-id="994c4-115">V následující tabulce jsou uvedeny běžné verze systému Windows pro podsystém.</span><span class="sxs-lookup"><span data-stu-id="994c4-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="994c4-116">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="994c4-116">Windows version</span></span>|<span data-ttu-id="994c4-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="994c4-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="994c4-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="994c4-118">Windows 2000</span></span>|<span data-ttu-id="994c4-119">5.00</span><span class="sxs-lookup"><span data-stu-id="994c4-119">5.00</span></span>|
|<span data-ttu-id="994c4-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="994c4-120">Windows XP</span></span>|<span data-ttu-id="994c4-121">5.01</span><span class="sxs-lookup"><span data-stu-id="994c4-121">5.01</span></span>|
|<span data-ttu-id="994c4-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="994c4-122">Windows Server 2003</span></span>|<span data-ttu-id="994c4-123">5.02</span><span class="sxs-lookup"><span data-stu-id="994c4-123">5.02</span></span>|
|<span data-ttu-id="994c4-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="994c4-124">Windows Vista</span></span>|<span data-ttu-id="994c4-125">6.00</span><span class="sxs-lookup"><span data-stu-id="994c4-125">6.00</span></span>|
|<span data-ttu-id="994c4-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="994c4-126">Windows 7</span></span>|<span data-ttu-id="994c4-127">6.01</span><span class="sxs-lookup"><span data-stu-id="994c4-127">6.01</span></span>|
|<span data-ttu-id="994c4-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="994c4-128">Windows Server 2008</span></span>|<span data-ttu-id="994c4-129">6.01</span><span class="sxs-lookup"><span data-stu-id="994c4-129">6.01</span></span>|
|<span data-ttu-id="994c4-130">Windows 8</span><span class="sxs-lookup"><span data-stu-id="994c4-130">Windows 8</span></span>|<span data-ttu-id="994c4-131">6.02</span><span class="sxs-lookup"><span data-stu-id="994c4-131">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="994c4-132">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="994c4-132">Default values</span></span>

<span data-ttu-id="994c4-133">Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="994c4-133">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="994c4-134">Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="994c4-134">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="994c4-135">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="994c4-135">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="994c4-136">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="994c4-136">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="994c4-137">-platforma:rameno</span><span class="sxs-lookup"><span data-stu-id="994c4-137">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="994c4-138">Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte na rozhraní .NET Framework 4.5 a nenastavili jste žádné možnosti kompilátoru, které byly zadány dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="994c4-138">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="994c4-139">Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek je true.</span><span class="sxs-lookup"><span data-stu-id="994c4-139">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="994c4-140">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="994c4-140">Setting this option</span></span>

<span data-ttu-id="994c4-141">Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, musíte `SubsystemVersion` otevřít soubor .csproj a zadat hodnotu vlastnosti v xml MSBuild.</span><span class="sxs-lookup"><span data-stu-id="994c4-141">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="994c4-142">Tuto možnost nelze nastavit v ide sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="994c4-142">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="994c4-143">Další informace naleznete v tématu "Výchozí hodnoty" dříve v tomto tématu nebo [společné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="994c4-143">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="994c4-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="994c4-144">See also</span></span>

- [<span data-ttu-id="994c4-145">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="994c4-145">C# Compiler Options</span></span>](./index.md)
