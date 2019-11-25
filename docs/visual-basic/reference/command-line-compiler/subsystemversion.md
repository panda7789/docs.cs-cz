---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: a977bc4cff822de551bf82d0f31707e9b2b6ea41
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348540"
---
# <a name="-subsystemversion-visual-basic"></a><span data-ttu-id="2dca4-102">-subsystemversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dca4-102">-subsystemversion (Visual Basic)</span></span>

<span data-ttu-id="2dca4-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span><span class="sxs-lookup"><span data-stu-id="2dca4-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="2dca4-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span><span class="sxs-lookup"><span data-stu-id="2dca4-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="2dca4-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span><span class="sxs-lookup"><span data-stu-id="2dca4-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dca4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dca4-106">Syntax</span></span>

```vb
-subsystemversion:major.minor
```

## <a name="parameters"></a><span data-ttu-id="2dca4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2dca4-107">Parameters</span></span>

`major.minor`

<span data-ttu-id="2dca4-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span><span class="sxs-lookup"><span data-stu-id="2dca4-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="2dca4-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span><span class="sxs-lookup"><span data-stu-id="2dca4-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="2dca4-110">You must specify the values for `major` and `minor` as integers.</span><span class="sxs-lookup"><span data-stu-id="2dca4-110">You must specify the values for `major` and `minor` as integers.</span></span>

<span data-ttu-id="2dca4-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span><span class="sxs-lookup"><span data-stu-id="2dca4-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="2dca4-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span><span class="sxs-lookup"><span data-stu-id="2dca4-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="2dca4-113">We recommend expressing the minor version as two digits to avoid confusion.</span><span class="sxs-lookup"><span data-stu-id="2dca4-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>

## <a name="remarks"></a><span data-ttu-id="2dca4-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2dca4-114">Remarks</span></span>

<span data-ttu-id="2dca4-115">The following table lists common subsystem versions of Windows.</span><span class="sxs-lookup"><span data-stu-id="2dca4-115">The following table lists common subsystem versions of Windows.</span></span>

|<span data-ttu-id="2dca4-116">Windows version</span><span class="sxs-lookup"><span data-stu-id="2dca4-116">Windows version</span></span>|<span data-ttu-id="2dca4-117">Subsystem version</span><span class="sxs-lookup"><span data-stu-id="2dca4-117">Subsystem version</span></span>|
|---------------------|-----------------------|
|<span data-ttu-id="2dca4-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="2dca4-118">Windows 2000</span></span>|<span data-ttu-id="2dca4-119">5.00</span><span class="sxs-lookup"><span data-stu-id="2dca4-119">5.00</span></span>|
|<span data-ttu-id="2dca4-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="2dca4-120">Windows XP</span></span>|<span data-ttu-id="2dca4-121">5.01</span><span class="sxs-lookup"><span data-stu-id="2dca4-121">5.01</span></span>|
|<span data-ttu-id="2dca4-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="2dca4-122">Windows Server 2003</span></span>|<span data-ttu-id="2dca4-123">5.02</span><span class="sxs-lookup"><span data-stu-id="2dca4-123">5.02</span></span>|
|<span data-ttu-id="2dca4-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="2dca4-124">Windows Vista</span></span>|<span data-ttu-id="2dca4-125">6.00</span><span class="sxs-lookup"><span data-stu-id="2dca4-125">6.00</span></span>|
|<span data-ttu-id="2dca4-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="2dca4-126">Windows 7</span></span>|<span data-ttu-id="2dca4-127">6.01</span><span class="sxs-lookup"><span data-stu-id="2dca4-127">6.01</span></span>|
|<span data-ttu-id="2dca4-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="2dca4-128">Windows Server 2008</span></span>|<span data-ttu-id="2dca4-129">6.01</span><span class="sxs-lookup"><span data-stu-id="2dca4-129">6.01</span></span>|
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="2dca4-130">6.02</span><span class="sxs-lookup"><span data-stu-id="2dca4-130">6.02</span></span>|

## <a name="default-values"></a><span data-ttu-id="2dca4-131">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="2dca4-131">Default values</span></span>

<span data-ttu-id="2dca4-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span><span class="sxs-lookup"><span data-stu-id="2dca4-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>

- <span data-ttu-id="2dca4-133">The default value is 6.02 if any compiler option in the following list is set:</span><span class="sxs-lookup"><span data-stu-id="2dca4-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>

  - [<span data-ttu-id="2dca4-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="2dca4-134">-target:appcontainerexe</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="2dca4-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="2dca4-135">-target:winmdobj</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)

  - [<span data-ttu-id="2dca4-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="2dca4-136">-platform:arm</span></span>](../../../visual-basic/reference/command-line-compiler/platform.md)

- <span data-ttu-id="2dca4-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span><span class="sxs-lookup"><span data-stu-id="2dca4-137">The default value is 6.00 if you're using MSBuild, you're targeting .NET Framework 4.5, and you haven't set any of the compiler options that were specified earlier in this list.</span></span>

- <span data-ttu-id="2dca4-138">The default value is 4.00 if none of the previous conditions is true.</span><span class="sxs-lookup"><span data-stu-id="2dca4-138">The default value is 4.00 if none of the previous conditions is true.</span></span>

## <a name="setting-this-option"></a><span data-ttu-id="2dca4-139">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="2dca4-139">Setting this option</span></span>

<span data-ttu-id="2dca4-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span><span class="sxs-lookup"><span data-stu-id="2dca4-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .vbproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="2dca4-141">You can't set this option in the Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="2dca4-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="2dca4-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="2dca4-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="see-also"></a><span data-ttu-id="2dca4-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dca4-143">See also</span></span>

- [<span data-ttu-id="2dca4-144">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="2dca4-144">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)

- [<span data-ttu-id="2dca4-145">Vlastnosti nástroje MSBuild</span><span class="sxs-lookup"><span data-stu-id="2dca4-145">MSBuild Properties</span></span>](/visualstudio/msbuild/msbuild-properties)
