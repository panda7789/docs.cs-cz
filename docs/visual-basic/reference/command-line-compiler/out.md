---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352378"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="13611-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13611-102">-out (Visual Basic)</span></span>
<span data-ttu-id="13611-103">Specifies the name of the output file.</span><span class="sxs-lookup"><span data-stu-id="13611-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13611-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13611-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="13611-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="13611-105">Arguments</span></span>  
  
|<span data-ttu-id="13611-106">Termín</span><span class="sxs-lookup"><span data-stu-id="13611-106">Term</span></span>|<span data-ttu-id="13611-107">Definice</span><span class="sxs-lookup"><span data-stu-id="13611-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="13611-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="13611-108">Required.</span></span> <span data-ttu-id="13611-109">The name of the output file the compiler creates.</span><span class="sxs-lookup"><span data-stu-id="13611-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="13611-110">If the file name contains a space, enclose the name in quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="13611-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13611-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13611-111">Remarks</span></span>  
 <span data-ttu-id="13611-112">Specify the full name and extension of the file to create.</span><span class="sxs-lookup"><span data-stu-id="13611-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="13611-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span><span class="sxs-lookup"><span data-stu-id="13611-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="13611-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span><span class="sxs-lookup"><span data-stu-id="13611-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="13611-115">To set -out in the Visual Studio integrated development environment</span><span class="sxs-lookup"><span data-stu-id="13611-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="13611-116">1.  Have a project selected in **Solution Explorer**.</span><span class="sxs-lookup"><span data-stu-id="13611-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="13611-117">On the **Project** menu, click **Properties**.</span><span class="sxs-lookup"><span data-stu-id="13611-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="13611-118">2.  Click the **Application** tab.</span><span class="sxs-lookup"><span data-stu-id="13611-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="13611-119">3.  Modify the value in the **Assembly Name** box.</span><span class="sxs-lookup"><span data-stu-id="13611-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="13611-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="13611-120">Example</span></span>  
 <span data-ttu-id="13611-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="13611-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="13611-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13611-122">See also</span></span>

- [<span data-ttu-id="13611-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="13611-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="13611-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13611-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="13611-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="13611-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
