---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 35e02d1ad4409e754c2466f7d0ae7e68214772e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716695"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="97ad5-102">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97ad5-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="97ad5-103">Způsobí, že kompilátor provede informace o typech v zadaných sestaveních, které jsou k dispozici pro projekt, který právě kompilujete.</span><span class="sxs-lookup"><span data-stu-id="97ad5-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97ad5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97ad5-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="97ad5-105">nebo</span><span class="sxs-lookup"><span data-stu-id="97ad5-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="97ad5-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="97ad5-106">Arguments</span></span>  
  
|<span data-ttu-id="97ad5-107">Termín</span><span class="sxs-lookup"><span data-stu-id="97ad5-107">Term</span></span>|<span data-ttu-id="97ad5-108">Definice</span><span class="sxs-lookup"><span data-stu-id="97ad5-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="97ad5-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="97ad5-109">Required.</span></span> <span data-ttu-id="97ad5-110">Seznam názvů souborů sestavení oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="97ad5-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="97ad5-111">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek.</span><span class="sxs-lookup"><span data-stu-id="97ad5-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97ad5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97ad5-112">Remarks</span></span>  
 <span data-ttu-id="97ad5-113">Soubory, které importujete, musí obsahovat metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="97ad5-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="97ad5-114">Mimo sestavení jsou viditelné pouze veřejné typy.</span><span class="sxs-lookup"><span data-stu-id="97ad5-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="97ad5-115">Možnost [-addmodule –](../../../visual-basic/reference/command-line-compiler/addmodule.md) Importuje metadata z modulu.</span><span class="sxs-lookup"><span data-stu-id="97ad5-115">The [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="97ad5-116">Pokud odkazujete na sestavení (sestavení A), které odkazuje na jiné sestavení (sestavení B), musíte odkazovat na sestavení B, pokud:</span><span class="sxs-lookup"><span data-stu-id="97ad5-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="97ad5-117">Typ ze sestavení A dědí z typu nebo implementuje rozhraní ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="97ad5-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="97ad5-118">Je vyvoláno pole, vlastnost, událost nebo metoda, které mají návratový typ nebo typ parametru ze sestavení B.</span><span class="sxs-lookup"><span data-stu-id="97ad5-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="97ad5-119">Pomocí [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) Určete adresář, ve kterém je umístěn jeden nebo více odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="97ad5-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="97ad5-120">Aby kompilátor rozpoznal typ v sestavení (ne v modulu), musí být vynucen přeložit typ.</span><span class="sxs-lookup"><span data-stu-id="97ad5-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="97ad5-121">Jedním z příkladů toho, jak to lze provést, je definovat instanci typu.</span><span class="sxs-lookup"><span data-stu-id="97ad5-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="97ad5-122">Další způsoby jsou k dispozici pro překlad názvů typů v sestavení pro kompilátor.</span><span class="sxs-lookup"><span data-stu-id="97ad5-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="97ad5-123">Například Pokud převezmete z typu v sestavení, název typu je poté pro kompilátor znám.</span><span class="sxs-lookup"><span data-stu-id="97ad5-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="97ad5-124">Ve výchozím nastavení se používá soubor odezvy Vbc. rsp, který odkazuje na běžně používaná .NET Framework sestavení.</span><span class="sxs-lookup"><span data-stu-id="97ad5-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="97ad5-125">Použijte `-noconfig`, pokud nechcete, aby kompilátor používal Vbc. rsp.</span><span class="sxs-lookup"><span data-stu-id="97ad5-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="97ad5-126">Krátká forma `-reference` je `-r`.</span><span class="sxs-lookup"><span data-stu-id="97ad5-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ad5-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="97ad5-127">Example</span></span>  
 <span data-ttu-id="97ad5-128">Následující příkaz zkompiluje zdrojový soubor `Input.vb` a referenční sestavení z `Metad1.dll` a `Metad2.dll` k výrobě `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="97ad5-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="97ad5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97ad5-129">See also</span></span>

- [<span data-ttu-id="97ad5-130">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="97ad5-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="97ad5-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="97ad5-131">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="97ad5-132">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97ad5-132">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="97ad5-133">Public</span><span class="sxs-lookup"><span data-stu-id="97ad5-133">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="97ad5-134">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="97ad5-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
