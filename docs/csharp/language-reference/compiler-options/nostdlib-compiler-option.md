---
title: -nostdlib (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 486539d7abdc3e65847a0bc0e228b1b20a2b2c37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602684"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="54449-102">-nostdlib (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="54449-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="54449-103">**-nostdlib** zabraňuje importu knihovny mscorlib. dll, která definuje celý obor názvů System.</span><span class="sxs-lookup"><span data-stu-id="54449-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="54449-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54449-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="54449-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54449-105">Remarks</span></span>

<span data-ttu-id="54449-106">Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému.</span><span class="sxs-lookup"><span data-stu-id="54449-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="54449-107">Pokud nezadáte **-nostdlib**, mscorlib. dll se naimportuje do programu (totéž jako určení **-nostdlib-** ).</span><span class="sxs-lookup"><span data-stu-id="54449-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="54449-108">Zadání **-nostdlib** je stejné jako zadání **-nostdlib +** .</span><span class="sxs-lookup"><span data-stu-id="54449-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="54449-109">Nastavení této možnosti kompilátoru v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="54449-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="54449-110">Následující pokyny platí pouze pro Visual Studio 2015 (a starší verze).</span><span class="sxs-lookup"><span data-stu-id="54449-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="54449-111">Vlastnost sestavení neodkazování **mscorlib. dll** v aplikaci Visual Studio 2017 neexistuje.</span><span class="sxs-lookup"><span data-stu-id="54449-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="54449-112">Otevřete stránku **vlastností** projektu.</span><span class="sxs-lookup"><span data-stu-id="54449-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="54449-113">Klikněte na stránku vlastností **sestavení** .</span><span class="sxs-lookup"><span data-stu-id="54449-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="54449-114">Klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="54449-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="54449-115">Upravte vlastnost Neodkazovat na knihovnu **mscorlib. dll** .</span><span class="sxs-lookup"><span data-stu-id="54449-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="54449-116">Programové nastavení tohoto parametru kompilátoru</span><span class="sxs-lookup"><span data-stu-id="54449-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="54449-117">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="54449-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="54449-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54449-118">See also</span></span>

- [<span data-ttu-id="54449-119">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="54449-119">C# Compiler Options</span></span>](./index.md)
