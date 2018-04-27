---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f098dd04b457b7db008788bcfb141af3f69843f8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="69481-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69481-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="69481-103">Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="69481-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69481-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69481-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="69481-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="69481-105">Arguments</span></span>  
  
|<span data-ttu-id="69481-106">Termín</span><span class="sxs-lookup"><span data-stu-id="69481-106">Term</span></span>|<span data-ttu-id="69481-107">Definice</span><span class="sxs-lookup"><span data-stu-id="69481-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="69481-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="69481-108">Required.</span></span> <span data-ttu-id="69481-109">Kompilátor používá znaková stránka určeného `id` interpretovat kódování zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="69481-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69481-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69481-110">Remarks</span></span>  
 <span data-ttu-id="69481-111">Kompilace zdrojového kódu uložit s konkrétním kódování, můžete použít `-codepage` k zadat znakovou stránku, která má být použita.</span><span class="sxs-lookup"><span data-stu-id="69481-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="69481-112">`-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="69481-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="69481-113">Další informace najdete v tématu [kódování znaků v rozhraní .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="69481-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="69481-114">`-codepage` Možnost není nutný v případě, že soubory zdrojového kódu se uložily pomocí aktuální znaková stránka ANSI, Unicode nebo UTF-8 podpisem.</span><span class="sxs-lookup"><span data-stu-id="69481-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="69481-115">Visual Studio uloží všechny soubory zdrojového kódu s aktuální znaková stránka ANSI ve výchozím nastavení, pokud uživatel zadá jiné kódování v **kódování** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="69481-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="69481-116">Visual Studio použije **kódování** dialogové okno otevřít soubory zdrojového kódu, které jsou uložené s jinou kódovou stránku.</span><span class="sxs-lookup"><span data-stu-id="69481-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69481-117">`-codepage` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="69481-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69481-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="69481-118">See Also</span></span>  
 [<span data-ttu-id="69481-119">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="69481-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
