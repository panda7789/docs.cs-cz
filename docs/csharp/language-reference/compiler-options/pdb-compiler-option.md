---
title: -PDB (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 3081f4716e8cd858d789db6050e635af941aa05c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602574"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="cc1a4-102">-PDB (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="cc1a4-102">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="cc1a4-103">Možnost kompilátoru **-PDB** Určuje název a umístění souboru se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="cc1a4-103">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc1a4-104">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc1a4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cc1a4-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="cc1a4-106">Název a umístění souboru se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="cc1a4-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc1a4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc1a4-107">Remarks</span></span>  
 <span data-ttu-id="cc1a4-108">Zadáte-li parametr [-C# Debug (možnosti kompilátoru)](./debug-compiler-option.md), kompilátor vytvoří soubor. pdb ve stejném adresáři, ve kterém kompilátor vytvoří výstupní soubor (. exe nebo. dll) s názvem souboru, který je stejný jako název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="cc1a4-108">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="cc1a4-109">**-PDB** umožňuje zadat jiný než výchozí název souboru a umístění pro soubor. pdb.</span><span class="sxs-lookup"><span data-stu-id="cc1a4-109">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="cc1a4-110">Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.</span><span class="sxs-lookup"><span data-stu-id="cc1a4-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1a4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc1a4-111">Example</span></span>  
 <span data-ttu-id="cc1a4-112">Zkompilujte `t.cs` a vytvořte soubor. pdb s názvem TT. pdb:</span><span class="sxs-lookup"><span data-stu-id="cc1a4-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc1a4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc1a4-113">See also</span></span>

- [<span data-ttu-id="cc1a4-114">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc1a4-114">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="cc1a4-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="cc1a4-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
