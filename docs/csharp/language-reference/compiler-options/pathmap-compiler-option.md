---
title: -pathmap (Možnosti kompilátoru Jazyka C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606623"
---
# <a name="-pathmap-c-compiler-options"></a><span data-ttu-id="67577-102">-pathmap (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="67577-102">-pathmap (C# Compiler Options)</span></span>

<span data-ttu-id="67577-103">Volba kompilátoru **-pathmap** určuje, jak mapovat fyzické cesty na zdrojové názvy cest, které kompilátor vyvodí.</span><span class="sxs-lookup"><span data-stu-id="67577-103">The **-pathmap** compiler option specifies how to map physical paths to source path names output by the compiler.</span></span>

## <a name="syntax"></a><span data-ttu-id="67577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67577-104">Syntax</span></span>

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a><span data-ttu-id="67577-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="67577-105">Arguments</span></span>

 <span data-ttu-id="67577-106">`path1`Úplná cesta ke zdrojovým souborům v aktuálním prostředí</span><span class="sxs-lookup"><span data-stu-id="67577-106">`path1` The full path to the source files in the current environment</span></span>

 <span data-ttu-id="67577-107">`sourcePath1`Zdrojová cesta nahrazená `path1` ve všech výstupních souborech.</span><span class="sxs-lookup"><span data-stu-id="67577-107">`sourcePath1` The source path substituted for `path1` in any output files.</span></span>

<span data-ttu-id="67577-108">Chcete-li určit více mapovaných zdrojových cest, oddělte je čárkou.</span><span class="sxs-lookup"><span data-stu-id="67577-108">To specify multiple mapped source paths, separate each with a comma.</span></span>

## <a name="remarks"></a><span data-ttu-id="67577-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67577-109">Remarks</span></span>

<span data-ttu-id="67577-110">Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="67577-110">The compiler writes the source path into its output for the following reasons:</span></span>

1. <span data-ttu-id="67577-111">Zdrojová cesta je nahrazena argumentem, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> pokud je použit a volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="67577-111">The source path is substituted for an argument when the <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> is applied to an optional parameter.</span></span>
1. <span data-ttu-id="67577-112">Zdrojová cesta je vložena do souboru PDB.</span><span class="sxs-lookup"><span data-stu-id="67577-112">The source path is embedded in a PDB file.</span></span>
1. <span data-ttu-id="67577-113">Cesta k souboru PDB je vložena do souboru PE (přenosný spustitelný) soubor.</span><span class="sxs-lookup"><span data-stu-id="67577-113">The path of the PDB file is embedded into a PE (portable executable) file.</span></span>

<span data-ttu-id="67577-114">Tato možnost mapuje každou fyzickou cestu v počítači, kde kompilátor běží na odpovídající cestu, která by měla být zapsána ve výstupních souborech.</span><span class="sxs-lookup"><span data-stu-id="67577-114">This option maps each physical path on the machine where the compiler runs to a corresponding path that should be written in the output files.</span></span>

## <a name="example"></a><span data-ttu-id="67577-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="67577-115">Example</span></span>

<span data-ttu-id="67577-116">Kompilace `t.cs` v adresáři **C:\\pracovní\\testy** a mapování tohoto adresáře na **\publish** ve výstupu:</span><span class="sxs-lookup"><span data-stu-id="67577-116">Compile `t.cs` in the directory **C:\\work\\tests** and map that directory to **\publish** in the output:</span></span>

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a><span data-ttu-id="67577-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="67577-117">See also</span></span>

- [<span data-ttu-id="67577-118">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67577-118">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="67577-119">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="67577-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
