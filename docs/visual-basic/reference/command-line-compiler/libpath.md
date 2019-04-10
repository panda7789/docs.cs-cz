---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b7bfcb0f2034145822922126fe61efea8d8ef269
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344205"
---
# <a name="-libpath"></a><span data-ttu-id="77b50-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="77b50-102">-libpath</span></span>
<span data-ttu-id="77b50-103">Určuje umístění odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="77b50-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77b50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77b50-104">Syntax</span></span>  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="77b50-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="77b50-105">Arguments</span></span>  
  
|<span data-ttu-id="77b50-106">Termín</span><span class="sxs-lookup"><span data-stu-id="77b50-106">Term</span></span>|<span data-ttu-id="77b50-107">Definice</span><span class="sxs-lookup"><span data-stu-id="77b50-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="77b50-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="77b50-108">Required.</span></span> <span data-ttu-id="77b50-109">Středníkem oddělený seznam adresářů pro kompilátor hledat v případě odkazovaných sestavení není nalezen v aktuálním pracovním adresáři (adresář, ze kterého je vyvolán kompilátor) nebo systémový adresář common language runtime.</span><span class="sxs-lookup"><span data-stu-id="77b50-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="77b50-110">Pokud název adresáře obsahuje mezery, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="77b50-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77b50-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77b50-111">Remarks</span></span>  
 <span data-ttu-id="77b50-112">`-libpath` Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="77b50-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="77b50-113">Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="77b50-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="77b50-114">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="77b50-114">Current working directory.</span></span> <span data-ttu-id="77b50-115">Toto je adresář, ze kterého je vyvolán kompilátor.</span><span class="sxs-lookup"><span data-stu-id="77b50-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="77b50-116">Common language runtime systémový adresář.</span><span class="sxs-lookup"><span data-stu-id="77b50-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="77b50-117">Adresáře určeného `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="77b50-117">Directories specified by `/libpath`.</span></span>  
  
4. <span data-ttu-id="77b50-118">Adresáře určené proměnnou prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="77b50-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="77b50-119">`-libpath` Možnost je sčítání; zadání více než jednou připojí k jakékoli předchozí hodnoty ho.</span><span class="sxs-lookup"><span data-stu-id="77b50-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="77b50-120">Použití `-reference` zadat odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="77b50-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="77b50-121">Chcete-li nastavit/Libpath v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="77b50-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="77b50-122">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="77b50-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="77b50-123">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="77b50-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="77b50-124">2.  Klikněte na tlačítko **odkazy** kartu.</span><span class="sxs-lookup"><span data-stu-id="77b50-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="77b50-125">3.  Klikněte na tlačítko **odkazují na cesty...**  tlačítko.</span><span class="sxs-lookup"><span data-stu-id="77b50-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="77b50-126">4.  V **cesty odkazů** dialogového okna zadejte název adresáře v **složky:** pole.</span><span class="sxs-lookup"><span data-stu-id="77b50-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="77b50-127">5.  Klikněte na tlačítko **přidat složku**.</span><span class="sxs-lookup"><span data-stu-id="77b50-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77b50-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="77b50-128">Example</span></span>  
 <span data-ttu-id="77b50-129">Následující kód zkompiluje `T2.vb` vytvořte soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="77b50-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="77b50-130">Kompilátor vyhledá v pracovním adresáři, v kořenovém adresáři jednotky C: a v adresáři nové sestavení jednotce C: pro odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="77b50-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="77b50-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77b50-131">See also</span></span>

- [<span data-ttu-id="77b50-132">Sestavení v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="77b50-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="77b50-133">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77b50-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="77b50-134">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="77b50-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
