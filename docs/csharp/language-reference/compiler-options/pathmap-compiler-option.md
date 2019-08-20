---
title: -pathmap (C# možnosti kompilátoru)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606623"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="b4e67-102">-pathmap (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="b4e67-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="b4e67-103">Možnost kompilátoru **-pathmap** určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="b4e67-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4e67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4e67-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="b4e67-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4e67-105">Arguments</span></span>

 <span data-ttu-id="b4e67-106">`path1`Úplná cesta ke zdrojovým souborům v aktuálním prostředí</span><span class="sxs-lookup"><span data-stu-id="b4e67-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="b4e67-107">`sourcePath1`Cesta ke zdroji nahrazena pro `path1` všechny výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="b4e67-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="b4e67-108">Chcete-li zadat více mapovaných zdrojových cest, oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="b4e67-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4e67-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4e67-109">Remarks</span></span>

<span data-ttu-id="b4e67-110">Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="b4e67-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="b4e67-111">Zdrojová cesta je nahrazena argumentem, pokud <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> je použita na volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4e67-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="b4e67-112">Zdrojová cesta je vložena do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="b4e67-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="b4e67-113">Cesta k souboru PDB je vložena do souboru PE (přenositelného spustitelného souboru).</span><span class="sxs-lookup"><span data-stu-id="b4e67-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="b4e67-114">Tato možnost mapuje každou fyzickou cestu v počítači, kde je kompilátor spuštěn, na odpovídající cestu, která by měla být zapsána do výstupních souborů.</span><span class="sxs-lookup"><span data-stu-id="b4e67-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="b4e67-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4e67-115">Example</span></span>

<span data-ttu-id="b4e67-116">Zkompilujte `t.cs` v adresáři **C:\\\\pracovní testy** a namapujte tento adresář na **\publish** ve výstupu:</span><span class="sxs-lookup"><span data-stu-id="b4e67-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="b4e67-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4e67-117">See also</span></span>

- [<span data-ttu-id="b4e67-118">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b4e67-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="b4e67-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b4e67-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
