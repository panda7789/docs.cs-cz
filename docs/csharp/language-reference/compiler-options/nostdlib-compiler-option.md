---
title: -nostdlib (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545826"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="b8d7c-102">-nostdlib (C# Compiler Options)</span><span class="sxs-lookup"><span data-stu-id="b8d7c-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="b8d7c-103">**-nostdlib** brání import mscorlib.dll, která definuje obor názvů celého systému.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8d7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8d7c-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="b8d7c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8d7c-105">Remarks</span></span>

<span data-ttu-id="b8d7c-106">Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="b8d7c-107">Pokud nezadáte **- nostdlib**, soubor mscorlib.dll je importována do programu (stejné jako zadání **- nostdlib –**).</span><span class="sxs-lookup"><span data-stu-id="b8d7c-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="b8d7c-108">Určení **- nostdlib** je stejné jako zadání **- nostdlib +**.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="b8d7c-109">Nastavení této možnosti kompilátoru v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b8d7c-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="b8d7c-110">Tyto pokyny platí pro Visual Studio 2015 (a starší verze) jenom.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="b8d7c-111">**Neodkazovat na mscorlib.dll** vlastnost sestavení neexistuje v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="b8d7c-112">Otevřít **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="b8d7c-113">Klikněte na tlačítko **sestavení** stránku vlastností.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="b8d7c-114">Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="b8d7c-115">Upravit **Neodkazovat na mscorlib.dll** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="b8d7c-116">Programové nastavení tohoto parametru kompilátoru</span><span class="sxs-lookup"><span data-stu-id="b8d7c-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="b8d7c-117">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8d7c-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d7c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8d7c-118">See also</span></span>

- [<span data-ttu-id="b8d7c-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b8d7c-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
