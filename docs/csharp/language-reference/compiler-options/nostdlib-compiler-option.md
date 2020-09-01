---
description: -nostdlib (možnosti kompilátoru C#)
title: -nostdlib (možnosti kompilátoru C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125095"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="8dbbe-103">-nostdlib (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="8dbbe-103">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="8dbbe-104">**-nostdlib** zabraňuje importu mscorlib.dll, který definuje celý obor názvů System.</span><span class="sxs-lookup"><span data-stu-id="8dbbe-104">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="8dbbe-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8dbbe-105">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="8dbbe-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dbbe-106">Remarks</span></span>

<span data-ttu-id="8dbbe-107">Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému.</span><span class="sxs-lookup"><span data-stu-id="8dbbe-107">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="8dbbe-108">Pokud nezadáte **-nostdlib**, mscorlib.dll se do programu importuje (totéž jako určení **-nostdlib-**).</span><span class="sxs-lookup"><span data-stu-id="8dbbe-108">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="8dbbe-109">Zadání **-nostdlib** je stejné jako zadání **-nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="8dbbe-109">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="8dbbe-110">Nastavení této možnosti kompilátoru v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8dbbe-110">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="8dbbe-111">Následující pokyny platí pouze pro Visual Studio 2015 (a starší verze).</span><span class="sxs-lookup"><span data-stu-id="8dbbe-111">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="8dbbe-112">Vlastnost do **Not reference mscorlib.dll** Build neexistuje v novějších verzích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8dbbe-112">The **Do not reference mscorlib.dll** build property doesn't exist in newer versions of Visual Studio.</span></span>

1. <span data-ttu-id="8dbbe-113">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="8dbbe-113">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="8dbbe-114">Klikněte na stránku vlastností **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="8dbbe-114">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="8dbbe-115">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="8dbbe-115">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="8dbbe-116">Upravte vlastnost **do not reference mscorlib.dll** .</span><span class="sxs-lookup"><span data-stu-id="8dbbe-116">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="8dbbe-117">Programové nastavení tohoto parametru kompilátoru</span><span class="sxs-lookup"><span data-stu-id="8dbbe-117">To set this compiler option programmatically</span></span>

<span data-ttu-id="8dbbe-118">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A> .</span><span class="sxs-lookup"><span data-stu-id="8dbbe-118">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="8dbbe-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dbbe-119">See also</span></span>

- [<span data-ttu-id="8dbbe-120">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="8dbbe-120">C# Compiler Options</span></span>](./index.md)
