---
title: /libpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2be2c460fddf2e8ea4fe1239ec073f208c072d34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="libpath"></a><span data-ttu-id="ece3a-102">/libpath</span><span class="sxs-lookup"><span data-stu-id="ece3a-102">/libpath</span></span>
<span data-ttu-id="ece3a-103">Určuje umístění odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="ece3a-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ece3a-104">Syntax</span></span>  
  
```  
/libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="ece3a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ece3a-105">Arguments</span></span>  
  
|<span data-ttu-id="ece3a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ece3a-106">Term</span></span>|<span data-ttu-id="ece3a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ece3a-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="ece3a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ece3a-108">Required.</span></span> <span data-ttu-id="ece3a-109">Seznam oddělený středníkem adresářů pro kompilátor hledat v případě odkazované sestavení nebyl nalezen v některém aktuální pracovní adresář (adresář, ze kterého je vyvolán kompilátor) nebo modul common language runtime systémového adresáře.</span><span class="sxs-lookup"><span data-stu-id="ece3a-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="ece3a-110">Pokud název adresáře obsahuje mezery, uzavřete název v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="ece3a-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ece3a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ece3a-111">Remarks</span></span>  
 <span data-ttu-id="ece3a-112">`/libpath` Možnost určuje umístění sestavení odkazuje [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.</span><span class="sxs-lookup"><span data-stu-id="ece3a-112">The `/libpath` option specifies the location of assemblies referenced by the [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="ece3a-113">Hledání kompilátoru pro odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="ece3a-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1.  <span data-ttu-id="ece3a-114">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="ece3a-114">Current working directory.</span></span> <span data-ttu-id="ece3a-115">Toto je adresář, ze kterého je vyvolán kompilátor.</span><span class="sxs-lookup"><span data-stu-id="ece3a-115">This is the directory from which the compiler is invoked.</span></span>  
  
2.  <span data-ttu-id="ece3a-116">Common language runtime systémového adresáře.</span><span class="sxs-lookup"><span data-stu-id="ece3a-116">The common language runtime system directory.</span></span>  
  
3.  <span data-ttu-id="ece3a-117">Adresáře určené `/libpath`.</span><span class="sxs-lookup"><span data-stu-id="ece3a-117">Directories specified by `/libpath`.</span></span>  
  
4.  <span data-ttu-id="ece3a-118">Adresáře určené proměnná prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="ece3a-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="ece3a-119">`/libpath` Možnost je sčítání; zadání je více než jednou připojí k jakékoli předchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ece3a-119">The `/libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="ece3a-120">Použití `/reference` zadat odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="ece3a-120">Use `/reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="ece3a-121">Chcete-li nastavit/Libpath v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="ece3a-121">To set /libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ece3a-122">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="ece3a-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ece3a-123">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ece3a-123">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="ece3a-124">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="ece3a-124">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="ece3a-125">2.  Klikněte **odkazy** kartě.</span><span class="sxs-lookup"><span data-stu-id="ece3a-125">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="ece3a-126">3.  Klikněte **odkazovat cesty...**  tlačítko.</span><span class="sxs-lookup"><span data-stu-id="ece3a-126">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="ece3a-127">4.  V **cesty odkazů** dialogovém okně zadejte název adresáře v **složky:** pole.</span><span class="sxs-lookup"><span data-stu-id="ece3a-127">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="ece3a-128">5.  Klikněte na tlačítko **přidat složku**.</span><span class="sxs-lookup"><span data-stu-id="ece3a-128">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ece3a-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ece3a-129">Example</span></span>  
 <span data-ttu-id="ece3a-130">Následující kód zkompiluje `T2.vb` k vytvoření souboru s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="ece3a-130">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="ece3a-131">Kompilátor vyhledá v pracovním adresáři, v kořenovém adresáři jednotky C: a v adresáři nové sestavení jednotky C: odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="ece3a-131">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```  
vbc /libpath:c:\;"c:\New Assemblies" /reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ece3a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ece3a-132">See Also</span></span>  
 [<span data-ttu-id="ece3a-133">Sestavení a globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="ece3a-133">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="ece3a-134">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ece3a-134">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ece3a-135">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="ece3a-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
