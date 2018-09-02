---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 8aee51df3ba9f92ca662fbbfbd73998e4a3b4538
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43405693"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="a6b80-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6b80-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="a6b80-103">Určuje znakovou stránku pro všechny soubory zdrojového kódu dané kompilace.</span><span class="sxs-lookup"><span data-stu-id="a6b80-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6b80-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6b80-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a6b80-105">Arguments</span></span>  
  
|<span data-ttu-id="a6b80-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a6b80-106">Term</span></span>|<span data-ttu-id="a6b80-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a6b80-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="a6b80-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a6b80-108">Required.</span></span> <span data-ttu-id="a6b80-109">Kompilátor používá znakovou stránku určené `id` k interpretaci kódování zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="a6b80-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6b80-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6b80-110">Remarks</span></span>  
 <span data-ttu-id="a6b80-111">Pro kompilaci zdrojového kódu s konkrétním kódováním, můžete použít `-codepage` chcete zadat znakovou stránku, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="a6b80-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="a6b80-112">`-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a6b80-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="a6b80-113">Další informace najdete v tématu [kódování znaků v rozhraní .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="a6b80-113">For more information, see [Character Encoding in the .NET Framework](https://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="a6b80-114">`-codepage` Možnost není nutná, pokud byly uloženy soubory zdrojového kódu pomocí aktuální znakové stránce ANSI, Unicode nebo UTF-8 s podpisem.</span><span class="sxs-lookup"><span data-stu-id="a6b80-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="a6b80-115">Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá, jiné kódování **kódování** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a6b80-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="a6b80-116">Visual Studio používá **kódování** dialogové okno otevřít soubory zdrojového kódu, které jsou uložené s jinou znakovou stránkou.</span><span class="sxs-lookup"><span data-stu-id="a6b80-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6b80-117">`-codepage` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a6b80-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b80-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6b80-118">See Also</span></span>  
 [<span data-ttu-id="a6b80-119">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a6b80-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
