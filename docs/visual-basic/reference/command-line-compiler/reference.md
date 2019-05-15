---
title: – referenční dokumentace (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 2394a23ddd59d09ce53c78fc4486fc5bae9e8516
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583358"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="528ed-102">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528ed-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="528ed-103">Způsobí, že kompilátor pro zpřístupnění informací o typu v zadaném sestavení pro projekt, který je aktuálně kompilován.</span><span class="sxs-lookup"><span data-stu-id="528ed-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="528ed-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="528ed-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="528ed-105">Arguments</span></span>  
  
|<span data-ttu-id="528ed-106">Termín</span><span class="sxs-lookup"><span data-stu-id="528ed-106">Term</span></span>|<span data-ttu-id="528ed-107">Definice</span><span class="sxs-lookup"><span data-stu-id="528ed-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="528ed-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="528ed-108">Required.</span></span> <span data-ttu-id="528ed-109">Čárkami oddělený seznam názvů souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="528ed-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="528ed-110">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="528ed-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528ed-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="528ed-111">Remarks</span></span>  
 <span data-ttu-id="528ed-112">Soubory, které importujete musí obsahovat metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="528ed-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="528ed-113">Pouze veřejné typy jsou viditelné mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="528ed-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="528ed-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.</span><span class="sxs-lookup"><span data-stu-id="528ed-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="528ed-115">Pokud odkazujete na sestavení (sestavení A) která sama odkazuje na jiné sestavení (sestavení B), budete muset odkaz na sestavení B, pokud:</span><span class="sxs-lookup"><span data-stu-id="528ed-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="528ed-116">Typ v sestavení A je odvozen z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="528ed-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="528ed-117">Pole, vlastnosti, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="528ed-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="528ed-118">Použití [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) určit adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="528ed-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="528ed-119">Kompilátor rozpoznával typ v sestavení (ne modul) musíte jej donutit k přeložení typu.</span><span class="sxs-lookup"><span data-stu-id="528ed-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="528ed-120">K definování instance typu je jeden příklad, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="528ed-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="528ed-121">Další možnosti jsou k dispozici přeložení názvů typů v sestavení pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="528ed-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="528ed-122">Například pokud je zděděn z typu v sestavení, název typu pak stane pro kompilátor známým.</span><span class="sxs-lookup"><span data-stu-id="528ed-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="528ed-123">Soubor odpovědí Vbc.rsp, který se odkazuje na běžně používá sestavení rozhraní .NET Framework, se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="528ed-123">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="528ed-124">Použít `-noconfig` Pokud nechcete, aby kompilátor používal Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="528ed-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="528ed-125">Krátký tvar `-reference` je `/r`.</span><span class="sxs-lookup"><span data-stu-id="528ed-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="528ed-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="528ed-126">Example</span></span>  
 <span data-ttu-id="528ed-127">Následující příkaz zkompiluje zdrojový soubor `Input.vb` a odkaz na sestavení z `Metad1.dll` a `Metad2.dll` k vytvoření `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="528ed-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="528ed-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="528ed-128">See also</span></span>

- [<span data-ttu-id="528ed-129">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="528ed-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="528ed-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="528ed-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="528ed-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="528ed-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="528ed-132">Public</span><span class="sxs-lookup"><span data-stu-id="528ed-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="528ed-133">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="528ed-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
