---
title: -nostdlib (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935521"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="d7a52-102">-nostdlib (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="d7a52-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="d7a52-103">**-nostdlib** brání import mscorlib.dll, která definuje obor názvů celého systému.</span><span class="sxs-lookup"><span data-stu-id="d7a52-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="d7a52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7a52-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="d7a52-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7a52-105">Remarks</span></span>

<span data-ttu-id="d7a52-106">Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty.</span><span class="sxs-lookup"><span data-stu-id="d7a52-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="d7a52-107">Pokud nezadáte **- nostdlib**, soubor mscorlib.dll je importována do programu (stejné jako zadání **- nostdlib –**).</span><span class="sxs-lookup"><span data-stu-id="d7a52-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="d7a52-108">Určení **- nostdlib** je stejné jako zadání **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="d7a52-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="d7a52-109">Nastavení této možnosti kompilátoru v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7a52-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="d7a52-110">Tyto pokyny platí pro Visual Studio 2015 (a starší verze) jenom.</span><span class="sxs-lookup"><span data-stu-id="d7a52-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="d7a52-111">**Neodkazovat na mscorlib.dll** vlastnost sestavení neexistuje v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d7a52-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="d7a52-112">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="d7a52-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="d7a52-113">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="d7a52-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="d7a52-114">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d7a52-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="d7a52-115">Upravit **Neodkazovat na mscorlib.dll** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d7a52-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="d7a52-116">Programové nastavení tohoto parametru kompilátoru</span><span class="sxs-lookup"><span data-stu-id="d7a52-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="d7a52-117">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="d7a52-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7a52-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7a52-118">See Also</span></span>

- [<span data-ttu-id="d7a52-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7a52-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
