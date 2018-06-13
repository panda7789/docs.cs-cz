---
title: -subsystemversion (možnosti kompilátoru C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: 25391dd504fb8a2b9458fd9495477258fc23d81a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215511"
---
# <a name="-subsystemversion-c-compiler-options"></a><span data-ttu-id="d08de-102">-subsystemversion (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d08de-102">-subsystemversion (C# Compiler Options)</span></span>
<span data-ttu-id="d08de-103">Určuje minimální verze subsystému, ve kterém můžete spustit vygenerovaný spustitelný soubor, a určení verze systému Windows, ve kterém můžete spustit spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="d08de-103">Specifies the minimum version of the subsystem on which the generated executable file can run, thereby determining the versions of Windows on which the executable file can run.</span></span> <span data-ttu-id="d08de-104">Nejčastěji tato možnost zajistí, že spustitelný soubor můžete využít funkce konkrétní zabezpečení, které nejsou k dispozici se staršími verzemi Windows.</span><span class="sxs-lookup"><span data-stu-id="d08de-104">Most commonly, this option ensures that the executable file can leverage particular security features that aren’t available with older versions of Windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d08de-105">Pokud chcete zadat subsystém sám sebe, použijte [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d08de-105">To specify the subsystem itself, use the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) compiler option.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d08de-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d08de-106">Syntax</span></span>  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d08de-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d08de-107">Parameters</span></span>  
 `major.minor`  
 <span data-ttu-id="d08de-108">Minimální požadovaná verze subsystému, jak je vyjádřen v s tečkami pro hlavní verze a podverze.</span><span class="sxs-lookup"><span data-stu-id="d08de-108">The minimum required version of the subsystem, as expressed in a dot notation for major and minor versions.</span></span> <span data-ttu-id="d08de-109">Například můžete zadat, že aplikace nelze spustit na operační systém, který je starší než Windows 7 Pokud nastavíte hodnotu tuto možnost na 6.01, podle popisu v tabulce dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="d08de-109">For example, you can specify that an application can't run on an operating system that's older than Windows 7 if you set the value of this option to 6.01, as the table later in this topic describes.</span></span> <span data-ttu-id="d08de-110">Je potřeba zadat hodnoty pro `major` a `minor` jako celá čísla.</span><span class="sxs-lookup"><span data-stu-id="d08de-110">You must specify the values for `major` and `minor` as integers.</span></span>  
  
 <span data-ttu-id="d08de-111">Program je zaměřen úvodní `minor` verze se nezmění na verzi, ale provést koncové nuly.</span><span class="sxs-lookup"><span data-stu-id="d08de-111">Leading zeroes in the `minor` version don't change the version, but trailing zeroes do.</span></span> <span data-ttu-id="d08de-112">Například 6.1 a 6.01 odkazovat na stejnou verzi, ale 6.10 odkazuje na jinou verzi.</span><span class="sxs-lookup"><span data-stu-id="d08de-112">For example, 6.1 and 6.01 refer to the same version, but 6.10 refers to a different version.</span></span> <span data-ttu-id="d08de-113">Doporučujeme, abyste vyjádření na podverzi jako dvě číslice k zamezení nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="d08de-113">We recommend expressing the minor version as two digits to avoid confusion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d08de-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d08de-114">Remarks</span></span>  
 <span data-ttu-id="d08de-115">V následující tabulce jsou uvedeny běžné subsystému verzích systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d08de-115">The following table lists common subsystem versions of Windows.</span></span>  
  
|<span data-ttu-id="d08de-116">Verze systému Windows</span><span class="sxs-lookup"><span data-stu-id="d08de-116">Windows version</span></span>|<span data-ttu-id="d08de-117">Verze subsystému</span><span class="sxs-lookup"><span data-stu-id="d08de-117">Subsystem version</span></span>|  
|---------------------|-----------------------|  
|<span data-ttu-id="d08de-118">Windows 2000</span><span class="sxs-lookup"><span data-stu-id="d08de-118">Windows 2000</span></span>|<span data-ttu-id="d08de-119">5.00</span><span class="sxs-lookup"><span data-stu-id="d08de-119">5.00</span></span>|  
|<span data-ttu-id="d08de-120">Windows XP</span><span class="sxs-lookup"><span data-stu-id="d08de-120">Windows XP</span></span>|<span data-ttu-id="d08de-121">5.01</span><span class="sxs-lookup"><span data-stu-id="d08de-121">5.01</span></span>|  
|<span data-ttu-id="d08de-122">Windows Server 2003</span><span class="sxs-lookup"><span data-stu-id="d08de-122">Windows Server 2003</span></span>|<span data-ttu-id="d08de-123">5.02</span><span class="sxs-lookup"><span data-stu-id="d08de-123">5.02</span></span>|  
|<span data-ttu-id="d08de-124">Windows Vista</span><span class="sxs-lookup"><span data-stu-id="d08de-124">Windows Vista</span></span>|<span data-ttu-id="d08de-125">6.00</span><span class="sxs-lookup"><span data-stu-id="d08de-125">6.00</span></span>|  
|<span data-ttu-id="d08de-126">Windows 7</span><span class="sxs-lookup"><span data-stu-id="d08de-126">Windows 7</span></span>|<span data-ttu-id="d08de-127">6.01</span><span class="sxs-lookup"><span data-stu-id="d08de-127">6.01</span></span>|  
|<span data-ttu-id="d08de-128">Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="d08de-128">Windows Server 2008</span></span>|<span data-ttu-id="d08de-129">6.01</span><span class="sxs-lookup"><span data-stu-id="d08de-129">6.01</span></span>|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|<span data-ttu-id="d08de-130">6.02</span><span class="sxs-lookup"><span data-stu-id="d08de-130">6.02</span></span>|  
  
## <a name="default-values"></a><span data-ttu-id="d08de-131">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="d08de-131">Default values</span></span>  
 <span data-ttu-id="d08de-132">Výchozí hodnota **- subsystemversion** – možnost kompilátoru závisí na podmínkách v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="d08de-132">The default value of the **-subsystemversion** compiler option depends on the conditions in the following list:</span></span>  
  
-   <span data-ttu-id="d08de-133">Výchozí hodnota je 6.02, pokud je nastavená žádné – možnost kompilátoru v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="d08de-133">The default value is 6.02 if any compiler option in the following list is set:</span></span>  
  
    -   [<span data-ttu-id="d08de-134">-target:appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="d08de-134">-target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [<span data-ttu-id="d08de-135">-target:winmdobj</span><span class="sxs-lookup"><span data-stu-id="d08de-135">-target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [<span data-ttu-id="d08de-136">-platform: arm</span><span class="sxs-lookup"><span data-stu-id="d08de-136">-platform:arm</span></span>](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   <span data-ttu-id="d08de-137">Výchozí hodnota je 6.00, pokud používáte nástroje MSBuild, jste cílení [!INCLUDE[net_v45](~/includes/net-v45-md.md)], a jste nenastavili některé z možností kompilátoru, která jste zadali dříve v tomto seznamu.</span><span class="sxs-lookup"><span data-stu-id="d08de-137">The default value is 6.00 if you're using MSBuild, you're targeting [!INCLUDE[net_v45](~/includes/net-v45-md.md)], and you haven't set any of the compiler options that were specified earlier in this list.</span></span>  
  
-   <span data-ttu-id="d08de-138">Výchozí hodnota je 4.00, pokud žádná z předchozích podmínek.</span><span class="sxs-lookup"><span data-stu-id="d08de-138">The default value is 4.00 if none of the previous conditions is true.</span></span>  
  
## <a name="setting-this-option"></a><span data-ttu-id="d08de-139">Nastavení této možnosti</span><span class="sxs-lookup"><span data-stu-id="d08de-139">Setting this option</span></span>  
 <span data-ttu-id="d08de-140">Chcete-li nastavit **- subsystemversion** – možnost kompilátoru ve Visual Studiu otevřete soubor .csproj a zadejte hodnotu pro `SubsystemVersion` vlastnost v souboru XML MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d08de-140">To set the **-subsystemversion** compiler option in Visual Studio, you must open the .csproj file and specify a value for the `SubsystemVersion` property in the MSBuild XML.</span></span> <span data-ttu-id="d08de-141">Tuto možnost nelze nastavit v integrovaném vývojovém prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d08de-141">You can't set this option in the Visual Studio IDE.</span></span> <span data-ttu-id="d08de-142">Další informace najdete v tématu "Výchozí hodnoty" dříve v tomto tématu nebo [běžné vlastnosti projektu nástroje MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="d08de-142">For more information, see "Default values" earlier in this topic or [Common MSBuild Project Properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d08de-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d08de-143">See Also</span></span>  
 [<span data-ttu-id="d08de-144">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d08de-144">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
