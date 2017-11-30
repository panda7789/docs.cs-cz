---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a><span data-ttu-id="c423e-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c423e-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="c423e-103">Způsobí, že kompilátor zpřístupnění informací o typu v zadaném sestavení do projektu, které jsou aktuálně kompilace.</span><span class="sxs-lookup"><span data-stu-id="c423e-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c423e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c423e-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="c423e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c423e-105">Arguments</span></span>  
  
|<span data-ttu-id="c423e-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c423e-106">Term</span></span>|<span data-ttu-id="c423e-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c423e-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="c423e-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c423e-108">Required.</span></span> <span data-ttu-id="c423e-109">Čárkami oddělený seznam názvů souborů sestavení.</span><span class="sxs-lookup"><span data-stu-id="c423e-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="c423e-110">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="c423e-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c423e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c423e-111">Remarks</span></span>  
 <span data-ttu-id="c423e-112">Soubory, které importujete musí obsahovat metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="c423e-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="c423e-113">Pouze veřejné typy jsou viditelné mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="c423e-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="c423e-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) možnost Importuje metadata z modulu.</span><span class="sxs-lookup"><span data-stu-id="c423e-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="c423e-115">Pokud odkazujete na sestavení (sestavení A) které se odkazuje na sestavení (sestavení B), budete muset odkaz na sestavení B, pokud:</span><span class="sxs-lookup"><span data-stu-id="c423e-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="c423e-116">Typu ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="c423e-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="c423e-117">Pole, vlastnost, události nebo metodu, která má návratový typ nebo parametr typu ze sestavení B je volána.</span><span class="sxs-lookup"><span data-stu-id="c423e-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="c423e-118">Použití [/Libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) na adresář, ve kterém se nachází jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="c423e-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="c423e-119">Kompilátor rozpoznat typu v sestavení (není modul) musí být vynutit pro vyřešení typu.</span><span class="sxs-lookup"><span data-stu-id="c423e-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="c423e-120">Jeden příklad, jak můžete k tomu je k definování instance typu.</span><span class="sxs-lookup"><span data-stu-id="c423e-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="c423e-121">Další způsoby jsou k dispozici pro překlad názvů typu v sestavení pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="c423e-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="c423e-122">Například pokud jste dědí od typu v sestavení, název typu pak určen kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c423e-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="c423e-123">Soubor odpovědí Vbc.rsp, jehož odkazy běžně používají [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení, se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c423e-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="c423e-124">Použít `/noconfig` Pokud nechcete, aby kompilátor používal Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="c423e-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="c423e-125">Zkratka pro `/reference` je `/r`.</span><span class="sxs-lookup"><span data-stu-id="c423e-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c423e-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="c423e-126">Example</span></span>  
 <span data-ttu-id="c423e-127">Následující kód zkompiluje zdrojový soubor `Input.vb` a odkaz na sestavení z `Metad1.dll` a `Metad2.dll` k vytvoření `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="c423e-127">The following code compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c423e-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c423e-128">See Also</span></span>  
 [<span data-ttu-id="c423e-129">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="c423e-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c423e-130">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="c423e-130">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="c423e-131">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c423e-131">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="c423e-132">Veřejné</span><span class="sxs-lookup"><span data-stu-id="c423e-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="c423e-133">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c423e-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
