---
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="64cea-102">-pathmap (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="64cea-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="64cea-103">**- Pathmap** – možnost kompilátoru určuje způsob namapování fyzické cesty k umístění zdroje cesta názvy výstupu kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="64cea-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="64cea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64cea-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="64cea-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="64cea-105">Arguments</span></span>

 <span data-ttu-id="64cea-106">`path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí</span><span class="sxs-lookup"><span data-stu-id="64cea-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="64cea-107">`sourcePath1` Zdrojová cesta nahrazena pro `path1` v jakékoli výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="64cea-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="64cea-108">Chcete-li určit víc cest namapované zdroje, oddělte každý oddělujte čárkami.</span><span class="sxs-lookup"><span data-stu-id="64cea-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="64cea-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64cea-109">Remarks</span></span>

<span data-ttu-id="64cea-110">Kompilátor zapisuje zdrojovou cestu cestu do jeho výstup z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="64cea-110">The compiler writes the source path path into its output for the following reasons:</span></span>

1. <span data-ttu-id="64cea-111">Zdrojová cesta je nahrazena pro argument při <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> se použije na volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="64cea-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="64cea-112">Zdrojová cesta je vložen do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="64cea-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="64cea-113">Cestu k souboru PDB vložené do souboru PE (přenosné spustitelný soubor).</span><span class="sxs-lookup"><span data-stu-id="64cea-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="64cea-114">Tato možnost mapuje každou fyzickou cestu v počítači, kde probíhá odpovídající cestu, která budou zasílány výstupní soubory kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="64cea-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="64cea-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="64cea-115">Example</span></span>

<span data-ttu-id="64cea-116">Kompilace `t.cs` v adresáři **C:\\pracovní\\testy** a mapovat tomuto adresáři svěřuje **\publish** ve výstupu:</span><span class="sxs-lookup"><span data-stu-id="64cea-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="64cea-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="64cea-117">See also</span></span>

 [<span data-ttu-id="64cea-118">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64cea-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="64cea-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="64cea-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
