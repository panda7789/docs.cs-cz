---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 9a5822a097828f818da020735c3822e86eb3236b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716640"
---
# <a name="-libpath"></a><span data-ttu-id="338d5-102">-libpath</span><span class="sxs-lookup"><span data-stu-id="338d5-102">-libpath</span></span>
<span data-ttu-id="338d5-103">Určuje umístění odkazovaných sestavení.</span><span class="sxs-lookup"><span data-stu-id="338d5-103">Specifies the location of referenced assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="338d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="338d5-104">Syntax</span></span>  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a><span data-ttu-id="338d5-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="338d5-105">Arguments</span></span>  
  
|<span data-ttu-id="338d5-106">Označení</span><span class="sxs-lookup"><span data-stu-id="338d5-106">Term</span></span>|<span data-ttu-id="338d5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="338d5-107">Definition</span></span>|  
|---|---|  
|`dirList`|<span data-ttu-id="338d5-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="338d5-108">Required.</span></span> <span data-ttu-id="338d5-109">Středníkem oddělený seznam adresářů, ve kterých se má kompilátor hledat, pokud odkazované sestavení nebylo nalezeno v aktuálním pracovním adresáři (adresář, ze kterého vyvoláváte kompilátor), nebo systémový adresář společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="338d5-109">Semicolon-delimited list of directories for the compiler to look in if a referenced assembly is not found in either the current working directory (the directory from which you are invoking the compiler) or the common language runtime's system directory.</span></span> <span data-ttu-id="338d5-110">Pokud název adresáře obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="338d5-110">If the directory name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="338d5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="338d5-111">Remarks</span></span>  
 <span data-ttu-id="338d5-112">`-libpath` Možnost určuje umístění sestavení, na které odkazuje možnost [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) .</span><span class="sxs-lookup"><span data-stu-id="338d5-112">The `-libpath` option specifies the location of assemblies referenced by the [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) option.</span></span>  
  
 <span data-ttu-id="338d5-113">Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:</span><span class="sxs-lookup"><span data-stu-id="338d5-113">The compiler searches for assembly references that are not fully qualified in the following order:</span></span>  
  
1. <span data-ttu-id="338d5-114">Aktuální pracovní adresář.</span><span class="sxs-lookup"><span data-stu-id="338d5-114">Current working directory.</span></span> <span data-ttu-id="338d5-115">Toto je adresář, ze kterého je kompilátor vyvolán.</span><span class="sxs-lookup"><span data-stu-id="338d5-115">This is the directory from which the compiler is invoked.</span></span>  
  
2. <span data-ttu-id="338d5-116">Systémový adresář společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="338d5-116">The common language runtime system directory.</span></span>  
  
3. <span data-ttu-id="338d5-117">Adresáře určené parametrem `-libpath`.</span><span class="sxs-lookup"><span data-stu-id="338d5-117">Directories specified by `-libpath`.</span></span>  
  
4. <span data-ttu-id="338d5-118">Adresáře určené proměnnou prostředí LIB.</span><span class="sxs-lookup"><span data-stu-id="338d5-118">Directories specified by the LIB environment variable.</span></span>  
  
 <span data-ttu-id="338d5-119">`-libpath` Možnost je aditivní; zadáním více než jednou se připojí k jakýmkoli předchozím hodnotám.</span><span class="sxs-lookup"><span data-stu-id="338d5-119">The `-libpath` option is additive; specifying it more than once appends to any prior values.</span></span>  
  
 <span data-ttu-id="338d5-120">Slouží `-reference` k zadání odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="338d5-120">Use `-reference` to specify an assembly reference.</span></span>  
  
|<span data-ttu-id="338d5-121">Nastavení-LIBPATH v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="338d5-121">To set -libpath in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="338d5-122">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="338d5-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="338d5-123">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="338d5-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="338d5-124">2. klikněte na kartu **odkazy** .</span><span class="sxs-lookup"><span data-stu-id="338d5-124">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="338d5-125">3. klikněte na tlačítko **cesty k odkazům...** .</span><span class="sxs-lookup"><span data-stu-id="338d5-125">3.  Click the **Reference Paths...** button.</span></span><br /><span data-ttu-id="338d5-126">4. v dialogovém okně **cesty k odkazům** zadejte název adresáře do pole **Složka:** .</span><span class="sxs-lookup"><span data-stu-id="338d5-126">4.  In the **Reference Paths** dialog box, enter the directory name in the **Folder:** box.</span></span><br /><span data-ttu-id="338d5-127">5. klikněte na **Přidat složku**.</span><span class="sxs-lookup"><span data-stu-id="338d5-127">5.  Click **Add Folder**.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="338d5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="338d5-128">Example</span></span>  
 <span data-ttu-id="338d5-129">Následující kód zkompiluje `T2.vb` pro vytvoření souboru. exe.</span><span class="sxs-lookup"><span data-stu-id="338d5-129">The following code compiles `T2.vb` to create an .exe file.</span></span> <span data-ttu-id="338d5-130">Kompilátor bude hledat v pracovním adresáři v kořenovém adresáři jednotky C: a v adresáři New Assemblies (sestavení) na jednotce C: pro odkazy na sestavení.</span><span class="sxs-lookup"><span data-stu-id="338d5-130">The compiler looks in the working directory, in the root directory of the C: drive, and in the New Assemblies directory of the C: drive for assembly references.</span></span>  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="338d5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="338d5-131">See also</span></span>

- [<span data-ttu-id="338d5-132">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="338d5-132">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="338d5-133">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="338d5-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="338d5-134">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="338d5-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
