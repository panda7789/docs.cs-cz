---
title: -subsystemversion (C# možnosti kompilátoru)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: f70389f87bf49ffccded4aef775c27ed0d034e1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922452"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="55171-102">-subsystemversion (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="55171-102">-subsystemversion (C# Compiler Options)</span></span>

<span data-ttu-id="55171-103">Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit.</span><span class="sxs-lookup"><span data-stu-id="55171-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="55171-104">Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="55171-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="55171-105">Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](./target-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="55171-105">To specify the subsystem itself, use the [-target](./target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="55171-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55171-106">Syntax</span></span>

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="55171-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="55171-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="55171-108">Minimální požadovaná verze subsystému, jak je vyjádřena v zápisu tečky pro hlavní a dílčí verze.</span><span class="sxs-lookup"><span data-stu-id="55171-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="55171-109">Například můžete určit, že aplikace nemůže běžet v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6,01, jak je popsáno v tabulce dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="55171-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="55171-110">Je nutné zadat hodnoty pro `major` a `minor` jako celé číslo.</span><span class="sxs-lookup"><span data-stu-id="55171-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="55171-111">Počáteční nuly ve `minor` verzi nemění verzi, ale mají na konci nula.</span><span class="sxs-lookup"><span data-stu-id="55171-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="55171-112">Například 6,1 a 6,01 odkazují na stejnou verzi, ale 6,10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="55171-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="55171-113">Pokud chcete zabránit nejasnostem, doporučujeme, abyste podverze vyjádřili jako dvě číslice.</span><span class="sxs-lookup"><span data-stu-id="55171-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="55171-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55171-114">Remarks</span></span>

<span data-ttu-id="55171-115">V následující tabulce jsou uvedeny běžné verze subsystému Windows.</span><span class="sxs-lookup"><span data-stu-id="55171-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="55171-116">Verze Windows</span><span class="sxs-lookup"><span data-stu-id="55171-116">Windows version</span></span>|<span data-ttu-id="55171-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="55171-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="55171-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="55171-118">Windows 2000</span></span>|<span data-ttu-id="55171-119">5.00</span><span class="sxs-lookup"><span data-stu-id="55171-119">5.00</span></span>|
|<span data-ttu-id="55171-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="55171-120">Windows XP</span></span>|<span data-ttu-id="55171-121">5.01</span><span class="sxs-lookup"><span data-stu-id="55171-121">5.01</span></span>|
|<span data-ttu-id="55171-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="55171-122">Windows Server 2003</span></span>|<span data-ttu-id="55171-123">5.02</span><span class="sxs-lookup"><span data-stu-id="55171-123">5.02</span></span>|
|<span data-ttu-id="55171-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="55171-124">Windows Vista</span></span>|<span data-ttu-id="55171-125">6.00</span><span class="sxs-lookup"><span data-stu-id="55171-125">6.00</span></span>|
|<span data-ttu-id="55171-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="55171-126">Windows 7</span></span>|<span data-ttu-id="55171-127">6.01</span><span class="sxs-lookup"><span data-stu-id="55171-127">6.01</span></span>|
|<span data-ttu-id="55171-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="55171-128">Windows Server 2008</span></span>|<span data-ttu-id="55171-129">6.01</span><span class="sxs-lookup"><span data-stu-id="55171-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="55171-130">6.02</span><span class="sxs-lookup"><span data-stu-id="55171-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="55171-131">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="55171-131">Default values</span></span>

<span data-ttu-id="55171-132">Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="55171-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="55171-133">Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="55171-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="55171-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="55171-134">-target:appcontainerexe</span></span>](./target-appcontainerexe-compiler-option.md)

  - [<span data-ttu-id="55171-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="55171-135">-target:winmdobj</span></span>](./target-winmdobj-compiler-option.md)

  - [<span data-ttu-id="55171-136">-Platforma: ARM</span><span class="sxs-lookup"><span data-stu-id="55171-136">-platform:arm</span></span>](./platform-compiler-option.md)

- <span data-ttu-id="55171-137">Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="55171-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="55171-138">Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.</span><span class="sxs-lookup"><span data-stu-id="55171-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="55171-139">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="55171-139">Setting this option</span></span>

<span data-ttu-id="55171-140">Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. csproj a zadat hodnotu `SubsystemVersion` vlastnosti v souboru XML nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="55171-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="55171-141">Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55171-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="55171-142">Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="55171-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="55171-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55171-143">See also</span></span>

- [<span data-ttu-id="55171-144">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55171-144">C# Compiler Options</span></span>](./index.md)
