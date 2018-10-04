---
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 277ab8e094f28fd5e3cbba4de12e742bb9614730
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583745"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="db79f-102">-pathmap (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="db79f-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="db79f-103">**- Pathmap** – možnost kompilátoru určuje způsob mapování fyzické cesty do zdrojové cesty názvy výstupu kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="db79f-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="db79f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db79f-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="db79f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="db79f-105">Arguments</span></span>

 <span data-ttu-id="db79f-106">`path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí</span><span class="sxs-lookup"><span data-stu-id="db79f-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="db79f-107">`sourcePath1` Zdrojová cesta nahrazené za `path1` v všechny výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="db79f-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="db79f-108">Chcete-li určit víc cest připojené zdroje, oddělte každou čárkou.</span><span class="sxs-lookup"><span data-stu-id="db79f-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="db79f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db79f-109">Remarks</span></span>

<span data-ttu-id="db79f-110">Kompilátor zapíše zdrojová_cesta_operačního_systému cestu do jeho výstup z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="db79f-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="db79f-111">Zdrojová cesta je nahrazen pro argument při <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> platí pro volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="db79f-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="db79f-112">Zdrojová cesta se vloží do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="db79f-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="db79f-113">Cesta k souboru PDB se vloží do souboru PE (portable executable).</span><span class="sxs-lookup"><span data-stu-id="db79f-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="db79f-114">Tato možnost mapuje každý fyzickou cestu na počítači, ve kterém kompilátor spuštěná na odpovídající cestu, která by měly být napsány v výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="db79f-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="db79f-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="db79f-115">Example</span></span>

<span data-ttu-id="db79f-116">Kompilace `t.cs` v adresáři **C:\\fungovat\\testy** a mapování tomuto adresáři **\publish** ve výstupu:</span><span class="sxs-lookup"><span data-stu-id="db79f-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="db79f-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db79f-117">See also</span></span>

- [<span data-ttu-id="db79f-118">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="db79f-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="db79f-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="db79f-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
