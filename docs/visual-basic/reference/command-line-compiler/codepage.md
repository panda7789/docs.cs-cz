---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 34dbf36cc79a8c4715cf6a07c57d559e14f40030
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363627"
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="20dfa-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20dfa-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="20dfa-103">Určuje znakovou stránku, která se má použít pro všechny soubory zdrojového kódu v kompilaci.</span><span class="sxs-lookup"><span data-stu-id="20dfa-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20dfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20dfa-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="20dfa-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="20dfa-105">Arguments</span></span>  
  
|<span data-ttu-id="20dfa-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="20dfa-106">Term</span></span>|<span data-ttu-id="20dfa-107">Definice</span><span class="sxs-lookup"><span data-stu-id="20dfa-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="20dfa-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="20dfa-108">Required.</span></span> <span data-ttu-id="20dfa-109">Kompilátor používá znakovou stránku určenou nástrojem `id` k interpretaci kódování zdrojových souborů.</span><span class="sxs-lookup"><span data-stu-id="20dfa-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20dfa-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20dfa-110">Remarks</span></span>  
 <span data-ttu-id="20dfa-111">Chcete-li zkompilovat zdrojový kód uložený pomocí konkrétního kódování, můžete použít `-codepage` k určení, která znaková stránka má být použita.</span><span class="sxs-lookup"><span data-stu-id="20dfa-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="20dfa-112">`-codepage`Možnost se vztahuje na všechny soubory zdrojového kódu ve vaší kompilaci.</span><span class="sxs-lookup"><span data-stu-id="20dfa-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="20dfa-113">Další informace naleznete v tématu [kódování znaků v .NET Framework](../../../standard/base-types/character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="20dfa-113">For more information, see [Character Encoding in the .NET Framework](../../../standard/base-types/character-encoding.md).</span></span>  
  
 <span data-ttu-id="20dfa-114">`-codepage`Možnost není nutná, pokud byly soubory zdrojového kódu uloženy pomocí aktuální znakové stránky ANSI, Unicode nebo UTF-8 s podpisem.</span><span class="sxs-lookup"><span data-stu-id="20dfa-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="20dfa-115">Visual Studio uloží všechny soubory zdrojového kódu s aktuální znakovou stránkou ANSI ve výchozím nastavení, pokud uživatel nezadá jiné kódování v dialogovém okně **kódování** .</span><span class="sxs-lookup"><span data-stu-id="20dfa-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="20dfa-116">Visual Studio používá dialogové okno **kódování** k otevření souborů zdrojového kódu uložených s jinou znakovou stránkou.</span><span class="sxs-lookup"><span data-stu-id="20dfa-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20dfa-117">Tato `-codepage` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="20dfa-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20dfa-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="20dfa-118">See also</span></span>

- [<span data-ttu-id="20dfa-119">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="20dfa-119">Visual Basic Command-Line Compiler</span></span>](index.md)
