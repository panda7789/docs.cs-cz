---
description: -PDB (možnosti kompilátoru C#)
title: -PDB (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
ms.openlocfilehash: 0dcafd0fd260488922c74a2330b312e80467e779
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124913"
---
# <a name="-pdb-c-compiler-options"></a><span data-ttu-id="c1120-103">-PDB (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="c1120-103">-pdb (C# Compiler Options)</span></span>
<span data-ttu-id="c1120-104">Možnost kompilátoru **-PDB** Určuje název a umístění souboru se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="c1120-104">The **-pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1120-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1120-105">Syntax</span></span>  
  
```console  
-pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c1120-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c1120-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c1120-107">Název a umístění souboru se symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="c1120-107">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1120-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1120-108">Remarks</span></span>  
 <span data-ttu-id="c1120-109">Zadáte-li parametr [-Debug (možnosti kompilátoru C#)](./debug-compiler-option.md), kompilátor vytvoří soubor. pdb ve stejném adresáři, ve kterém kompilátor vytvoří výstupní soubor (. exe nebo. dll) s názvem souboru, který je stejný jako název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="c1120-109">When you specify [-debug (C# Compiler Options)](./debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="c1120-110">**-PDB** umožňuje zadat jiný než výchozí název souboru a umístění pro soubor. pdb.</span><span class="sxs-lookup"><span data-stu-id="c1120-110">**-pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="c1120-111">Tuto možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani jej nelze změnit programově.</span><span class="sxs-lookup"><span data-stu-id="c1120-111">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1120-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1120-112">Example</span></span>  
 <span data-ttu-id="c1120-113">Zkompilujte `t.cs` a vytvořte soubor. pdb s názvem TT. pdb:</span><span class="sxs-lookup"><span data-stu-id="c1120-113">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc -debug -pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1120-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1120-114">See also</span></span>

- [<span data-ttu-id="c1120-115">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="c1120-115">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="c1120-116">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="c1120-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
