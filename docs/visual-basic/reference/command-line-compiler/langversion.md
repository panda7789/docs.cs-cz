---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793950"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="93c82-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93c82-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="93c82-103">Způsobí, že kompilátor tak, aby přijímal pouze syntaxi, která je zahrnutá v zadané verzi jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93c82-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c82-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="93c82-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="93c82-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="93c82-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="93c82-106">Required.</span></span> <span data-ttu-id="93c82-107">Jazykovou verzi používané během kompilace.</span><span class="sxs-lookup"><span data-stu-id="93c82-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="93c82-108">Platné hodnoty jsou `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` a `latest`.</span><span class="sxs-lookup"><span data-stu-id="93c82-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="93c82-109">Libovolné celé číslo můžete také zadat pomocí `.0` jako vedlejší verze, například `11.0`.</span><span class="sxs-lookup"><span data-stu-id="93c82-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="93c82-110">Zobrazí seznam všech možných hodnot tak, že zadáte `-langversion:?` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="93c82-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93c82-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93c82-111">Remarks</span></span>  
 <span data-ttu-id="93c82-112">`-langversion` Možnost určuje, jaké syntaxe kompilátor přijímá.</span><span class="sxs-lookup"><span data-stu-id="93c82-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="93c82-113">Například pokud chcete zadat, že je jazyková verze 9.0, kompilátor vygeneruje chyby syntaxe, která je platná pouze ve verzi 10.0 a novější.</span><span class="sxs-lookup"><span data-stu-id="93c82-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="93c82-114">Tuto možnost můžete použít při vývoji aplikací, které jiné cílové verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="93c82-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="93c82-115">Například pokud se zaměřujete na rozhraní .NET Framework 3.5, můžete použít tuto možnost k zajištění, že je velmi riskantní používat syntaxi z jazykové verze 10.0.</span><span class="sxs-lookup"><span data-stu-id="93c82-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="93c82-116">Můžete nastavit `-langversion` přímo pouze pomocí příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="93c82-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="93c82-117">Další informace najdete v tématu [cílení na konkrétní verzi rozhraní .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="93c82-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93c82-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="93c82-118">Example</span></span>  
 <span data-ttu-id="93c82-119">Následující kód zkompiluje `sample.vb` 9.0 jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="93c82-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="93c82-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93c82-120">See also</span></span>

- [<span data-ttu-id="93c82-121">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="93c82-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="93c82-122">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="93c82-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="93c82-123">Cílení na konkrétní verzi rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="93c82-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
