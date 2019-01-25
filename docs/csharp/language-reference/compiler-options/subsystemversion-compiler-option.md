---
title: -subsystemversion (možnosti kompilátoru C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 42d9d81c4cfbf98c1d7a470a5863ac9198f16395
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738076"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="0d384-102">-subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="0d384-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="0d384-103">Určuje minimální verzi subsystému, na kterém poběží vygenerovaný spustitelný soubor, a tím určení verze Windows, na kterém můžete spustit spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="0d384-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="0d384-104">Nejčastěji tato možnost zajišťuje, že spustitelného souboru, který můžete využít konkrétní bezpečnostní funkce, které nejsou k dispozici ve starších verzích Windows.</span><span class="sxs-lookup"><span data-stu-id="0d384-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d384-105">K určení subsystému, sama, použijte [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0d384-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d384-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d384-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d384-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="0d384-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="0d384-108">Minimální požadovaná verze subsystému, jak je vyjádřen v zápisu s tečkou pro hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="0d384-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="0d384-109">Například můžete určit, že aplikaci nelze spustit v operačním systému, který je starší než Windows 7. Pokud nastavíte na hodnotu této možnosti 6.01, podle popisu v tabulce dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0d384-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="0d384-110">Je nutné zadat hodnoty pro `major` a `minor` jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="0d384-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="0d384-111">Program je zaměřen nejlepší `minor` verze se nezmění na verzi, ale proveďte koncové nuly.</span><span class="sxs-lookup"><span data-stu-id="0d384-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="0d384-112">Například 6.1 a 6.01 odkazovat na stejnou verzi, ale 6.10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="0d384-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="0d384-113">Doporučujeme, abyste jako dvě číslice, aby nedocházelo k záměně vyjádření podverze.</span><span class="sxs-lookup"><span data-stu-id="0d384-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d384-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d384-114">Remarks</span></span>  
 <span data-ttu-id="0d384-115">Následující tabulka uvádí nejběžnější verze subsystému Windows.</span><span class="sxs-lookup"><span data-stu-id="0d384-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="0d384-116">Verze Windows</span><span class="sxs-lookup"><span data-stu-id="0d384-116">Windows version</span></span>|<span data-ttu-id="0d384-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="0d384-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="0d384-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="0d384-118">Windows 2000</span></span>|<span data-ttu-id="0d384-119">5.00</span><span class="sxs-lookup"><span data-stu-id="0d384-119">5.00</span></span>|  
|<span data-ttu-id="0d384-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="0d384-120">Windows XP</span></span>|<span data-ttu-id="0d384-121">5.01</span><span class="sxs-lookup"><span data-stu-id="0d384-121">5.01</span></span>|  
|<span data-ttu-id="0d384-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="0d384-122">Windows Server 2003</span></span>|<span data-ttu-id="0d384-123">5.02</span><span class="sxs-lookup"><span data-stu-id="0d384-123">5.02</span></span>|  
|<span data-ttu-id="0d384-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="0d384-124">Windows Vista</span></span>|<span data-ttu-id="0d384-125">6.00</span><span class="sxs-lookup"><span data-stu-id="0d384-125">6.00</span></span>|  
|<span data-ttu-id="0d384-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="0d384-126">Windows 7</span></span>|<span data-ttu-id="0d384-127">6.01</span><span class="sxs-lookup"><span data-stu-id="0d384-127">6.01</span></span>|  
|<span data-ttu-id="0d384-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="0d384-128">Windows Server 2008</span></span>|<span data-ttu-id="0d384-129">6.01</span><span class="sxs-lookup"><span data-stu-id="0d384-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="0d384-130">6.02</span><span class="sxs-lookup"><span data-stu-id="0d384-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="0d384-131">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="0d384-131">Default values</span></span>  
 <span data-ttu-id="0d384-132">Výchozí hodnota **- subsystemversion** – možnost kompilátoru závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="0d384-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="0d384-133">Výchozí hodnota je 6.02, je-li nastavit všechny možnosti kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="0d384-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="0d384-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="0d384-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="0d384-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="0d384-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="0d384-136">-platform:arm</span><span class="sxs-lookup"><span data-stu-id="0d384-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="0d384-137">Výchozí hodnota je 6.00, pokud používáte MSBuild, které cílíte [!INCLUDE[net_v45](~/includes/net-v45-md.md)], a jste nenastavili žádné možnosti kompilátoru, která jste zadali dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="0d384-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="0d384-138">Výchozí hodnota je 4.00, pokud žádná z předchozích podmínek není splněna.</span><span class="sxs-lookup"><span data-stu-id="0d384-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="0d384-139">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="0d384-139">Setting this option</span></span>  
 <span data-ttu-id="0d384-140">Chcete-li nastavit **- subsystemversion** – možnost kompilátoru v sadě Visual Studio, otevřete soubor .csproj a zadejte hodnotu pro `SubsystemVersion` vlastnost v XML nástroje MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0d384-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="0d384-141">Tuto možnost nelze nastavit v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d384-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="0d384-142">Další informace najdete v tématu "Výchozí hodnoty" výše v tomto tématu nebo [obecné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="0d384-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d384-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d384-143">See also</span></span>

- [<span data-ttu-id="0d384-144">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d384-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
