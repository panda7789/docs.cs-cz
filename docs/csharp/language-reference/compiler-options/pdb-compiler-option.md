---
title: -pdb (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602574"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="e7050-102">-pdb (Možnosti kompilátoru Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e7050-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="e7050-103">Možnost kompilátoru **-pdb** určuje název a umístění souboru ladicích symbolů.</span><span class="sxs-lookup"><span data-stu-id="e7050-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7050-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7050-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7050-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e7050-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="e7050-106">Název a umístění souboru ladicích symbolů.</span><span class="sxs-lookup"><span data-stu-id="e7050-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7050-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7050-107">Remarks</span></span>  
 <span data-ttu-id="e7050-108">Když zadáte [-debug (C# Compiler Options),](./debug-compiler-option.md)kompilátor vytvoří soubor PDB ve stejném adresáři, kde kompilátor vytvoří výstupní soubor (.exe nebo .dll) s názvem souboru, který je stejný jako název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="e7050-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="e7050-109">**-pdb** umožňuje zadat název a umístění souboru PDB, který není výchozí.</span><span class="sxs-lookup"><span data-stu-id="e7050-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="e7050-110">Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji nelze programově změnit.</span><span class="sxs-lookup"><span data-stu-id="e7050-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7050-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7050-111">Example</span></span>  
 <span data-ttu-id="e7050-112">Kompilace `t.cs` a vytvoření souboru PDB s názvem tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="e7050-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7050-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7050-113">See also</span></span>

- [<span data-ttu-id="e7050-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e7050-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e7050-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="e7050-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
