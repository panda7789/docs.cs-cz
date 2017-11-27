---
title: "-pdb (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 108244d7de49c2ff4df1ac7202e77958743b32df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="pdb-c-compiler-options"></a><span data-ttu-id="88779-102">/pdb (Možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="88779-102">/pdb (C# Compiler Options)</span></span>
<span data-ttu-id="88779-103">**/PDB** – možnost kompilátoru Určuje název a umístění souboru pro symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="88779-103">The **/pdb** compiler option specifies the name and location of the debug symbols file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88779-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88779-104">Syntax</span></span>  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="88779-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="88779-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="88779-106">Název a umístění souboru pro symboly ladění.</span><span class="sxs-lookup"><span data-stu-id="88779-106">The name and location of the debug symbols file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88779-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88779-107">Remarks</span></span>  
 <span data-ttu-id="88779-108">Pokud zadáte [/Debug (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), kompilátor vytvoří soubor .pdb ve stejném adresáři, kde bude vytvořen výstupní soubor (.exe nebo .dll) s názvem souboru, který je stejný jako název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="88779-108">When you specify [/debug (C# Compiler Options)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), the compiler will create a .pdb file in the same directory where the compiler will create the output file (.exe or .dll) with a file name that is the same as the name of the output file.</span></span>  
  
 <span data-ttu-id="88779-109">**/ pdb** vám umožní určit jiné než výchozí název souboru a umístění souboru pdb.</span><span class="sxs-lookup"><span data-stu-id="88779-109">**/pdb** allows you to specify a non-default file name and location for the .pdb file.</span></span>  
  
 <span data-ttu-id="88779-110">Tato možnost kompilátoru nelze nastavit ve vývojovém prostředí sady Visual Studio, ani ji není možné změnit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="88779-110">This compiler option cannot be set in the Visual Studio development environment, nor can it be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88779-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="88779-111">Example</span></span>  
 <span data-ttu-id="88779-112">Kompilace `t.cs` a vytvoří soubor .pdb s názvem tt.pdb:</span><span class="sxs-lookup"><span data-stu-id="88779-112">Compile `t.cs` and create a .pdb file called tt.pdb:</span></span>  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="88779-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="88779-113">See Also</span></span>  
 [<span data-ttu-id="88779-114">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="88779-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="88779-115">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="88779-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
