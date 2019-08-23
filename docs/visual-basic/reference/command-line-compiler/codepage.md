---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 3a5974a910303f847679f18c23e00cfaa00caa2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962617"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="8c16c-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c16c-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="8c16c-103">Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="8c16c-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c16c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c16c-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8c16c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8c16c-105">Arguments</span></span>  
  
|<span data-ttu-id="8c16c-106">Termín</span><span class="sxs-lookup"><span data-stu-id="8c16c-106">Term</span></span>|<span data-ttu-id="8c16c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="8c16c-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="8c16c-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8c16c-108">Required.</span></span> <span data-ttu-id="8c16c-109">Kompilátor používá znakovou stránku určenou nástrojem `id` k interpretaci kódování zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="8c16c-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c16c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c16c-110">Remarks</span></span>  
 <span data-ttu-id="8c16c-111">Chcete-li zkompilovat zdrojový kód uložený pomocí konkrétního kódování, `-codepage` můžete použít k určení, která znaková stránka má být použita.</span><span class="sxs-lookup"><span data-stu-id="8c16c-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="8c16c-112">`-codepage` Možnost se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.</span><span class="sxs-lookup"><span data-stu-id="8c16c-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="8c16c-113">Další informace naleznete v tématu [kódování znaků v .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="8c16c-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="8c16c-114">`-codepage` Možnost není nutná, pokud byly soubory zdrojového kódu uloženy pomocí aktuální znakové stránky ANSI, Unicode nebo UTF-8 s podpisem.</span><span class="sxs-lookup"><span data-stu-id="8c16c-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="8c16c-115">Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá jiné kódování v dialogovém okně **kódování** .</span><span class="sxs-lookup"><span data-stu-id="8c16c-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="8c16c-116">Visual Studio používá dialogové okno **kódování** k otevření souborů zdrojového kódu uložených s jinou znakovou stránkou.</span><span class="sxs-lookup"><span data-stu-id="8c16c-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c16c-117">Tato `-codepage` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="8c16c-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c16c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c16c-118">See also</span></span>

- [<span data-ttu-id="8c16c-119">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8c16c-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
