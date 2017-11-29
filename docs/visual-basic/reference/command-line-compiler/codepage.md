---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a><span data-ttu-id="a482a-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a482a-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="a482a-103">Určuje znakovou stránku pro všechny soubory zdrojového kódu v kompilace.</span><span class="sxs-lookup"><span data-stu-id="a482a-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a482a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a482a-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="a482a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a482a-105">Arguments</span></span>  
  
|<span data-ttu-id="a482a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a482a-106">Term</span></span>|<span data-ttu-id="a482a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a482a-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="a482a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="a482a-108">Required.</span></span> <span data-ttu-id="a482a-109">Kompilátor používá znaková stránka určeného `id` interpretovat kódování zdrojové soubory.</span><span class="sxs-lookup"><span data-stu-id="a482a-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a482a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a482a-110">Remarks</span></span>  
 <span data-ttu-id="a482a-111">Kompilace zdrojového kódu uložit s konkrétním kódování, můžete použít `/codepage` k zadat znakovou stránku, která má být použita.</span><span class="sxs-lookup"><span data-stu-id="a482a-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="a482a-112">`/codepage` Možnost se vztahuje na všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="a482a-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="a482a-113">Další informace najdete v tématu [kódování znaků v rozhraní .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span><span class="sxs-lookup"><span data-stu-id="a482a-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="a482a-114">`/codepage` Možnost není nutný v případě, že soubory zdrojového kódu se uložily pomocí aktuální znaková stránka ANSI, Unicode nebo UTF-8 podpisem.</span><span class="sxs-lookup"><span data-stu-id="a482a-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="a482a-115">uloží všechny soubory zdrojového kódu s aktuální znaková stránka ANSI ve výchozím nastavení, pokud uživatel zadá jiné kódování v **kódování** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="a482a-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="a482a-116">používá **kódování** dialogové okno otevřít soubory zdrojového kódu, které jsou uložené s jinou kódovou stránku.</span><span class="sxs-lookup"><span data-stu-id="a482a-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a482a-117">`/codepage` Možnost není k dispozici v rámci [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a482a-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a482a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a482a-118">See Also</span></span>  
 [<span data-ttu-id="a482a-119">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a482a-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
