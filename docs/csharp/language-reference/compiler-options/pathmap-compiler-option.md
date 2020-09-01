---
description: -pathmap (možnosti kompilátoru C#)
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125004"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="47d36-103">-pathmap (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="47d36-103">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="47d36-104">Možnost kompilátoru **-pathmap** určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="47d36-104">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="47d36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47d36-105">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="47d36-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="47d36-106">Arguments</span></span>

 <span data-ttu-id="47d36-107">`path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí</span><span class="sxs-lookup"><span data-stu-id="47d36-107">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="47d36-108">`sourcePath1` Cesta ke zdroji nahrazena pro `path1` všechny výstupní soubory.</span><span class="sxs-lookup"><span data-stu-id="47d36-108">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="47d36-109">Chcete-li zadat více mapovaných zdrojových cest, oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="47d36-109">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="47d36-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47d36-110">Remarks</span></span>

<span data-ttu-id="47d36-111">Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="47d36-111">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="47d36-112">Zdrojová cesta je nahrazena argumentem, pokud <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> je použita na volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="47d36-112">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="47d36-113">Zdrojová cesta je vložena do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="47d36-113">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="47d36-114">Cesta k souboru PDB je vložena do souboru PE (přenositelného spustitelného souboru).</span><span class="sxs-lookup"><span data-stu-id="47d36-114">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="47d36-115">Tato možnost mapuje každou fyzickou cestu v počítači, kde je kompilátor spuštěn, na odpovídající cestu, která by měla být zapsána do výstupních souborů.</span><span class="sxs-lookup"><span data-stu-id="47d36-115">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="47d36-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="47d36-116">Example</span></span>

<span data-ttu-id="47d36-117">Zkompilujte `t.cs` v adresáři **C: \\ pracovní \\ testy** a namapujte tento adresář na **\publish** ve výstupu:</span><span class="sxs-lookup"><span data-stu-id="47d36-117">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="47d36-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="47d36-118">See also</span></span>

- [<span data-ttu-id="47d36-119">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="47d36-119">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="47d36-120">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="47d36-120">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
