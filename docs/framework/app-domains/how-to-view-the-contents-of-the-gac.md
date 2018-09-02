---
title: 'Postupy: Zobrazení obsahu globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- GAC (global assembly cache), viewing contents
- list of assemblies in global assembly cache
- Global Assembly Cache tool
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3650de934cb3d2940d0e8e971d03aff856bddfd7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43394462"
---
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a><span data-ttu-id="217b7-102">Postupy: Zobrazení obsahu globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="217b7-102">How to: View the Contents of the Global Assembly Cache</span></span>
<span data-ttu-id="217b7-103">Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="217b7-103">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to view the contents of the global assembly cache.</span></span>  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="217b7-104">Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení</span><span class="sxs-lookup"><span data-stu-id="217b7-104">To view a list of the assemblies in the global assembly cache</span></span>  
  
1.  <span data-ttu-id="217b7-105">Na [příkazový řádek sady Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="217b7-105">At the [Visual Studio command prompt](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="217b7-106">**Gacutil -l** </span><span class="sxs-lookup"><span data-stu-id="217b7-106">**gacutil -l** </span></span>  
     <span data-ttu-id="217b7-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="217b7-107">-or-</span></span>  
    <span data-ttu-id="217b7-108">**Gacutil/l**</span><span class="sxs-lookup"><span data-stu-id="217b7-108">**gacutil /l**</span></span>  
  
 <span data-ttu-id="217b7-109">V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](https://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozšíření prostředí Windows umožňovalo zobrazení mezipaměti globálního sestavení v Průzkumníku souborů.</span><span class="sxs-lookup"><span data-stu-id="217b7-109">In earlier versions of the .NET Framework, the [Shfusion.dll](https://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) Windows shell extension enabled you to view the global assembly cache in File Explorer.</span></span> <span data-ttu-id="217b7-110">Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.</span><span class="sxs-lookup"><span data-stu-id="217b7-110">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll is obsolete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217b7-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="217b7-111">See Also</span></span>  
 [<span data-ttu-id="217b7-112">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="217b7-112">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="217b7-113">Gacutil.exe (nástroj globální mezipaměti sestavení)</span><span class="sxs-lookup"><span data-stu-id="217b7-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
