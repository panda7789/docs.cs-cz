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
# <a name="how-to-view-the-contents-of-the-global-assembly-cache"></a>Postupy: Zobrazení obsahu globální mezipaměti sestavení
Použití [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) k zobrazení obsahu globální mezipaměti sestavení.  
  
### <a name="to-view-a-list-of-the-assemblies-in-the-global-assembly-cache"></a>Chcete-li zobrazit seznam sestavení v globální mezipaměti sestavení  
  
1.  Na [příkazový řádek sady Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), zadejte následující příkaz:  
  
     **Gacutil -l**   
     -nebo-  
    **Gacutil/l**  
  
 V dřívějších verzích rozhraní .NET Framework [Shfusion.dll](https://msdn.microsoft.com/library/0d9464cf-ddba-4ca9-bbec-f678fb58f380) rozšíření prostředí Windows umožňovalo zobrazení mezipaměti globálního sestavení v Průzkumníku souborů. Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], je rozšíření Shfusion.dll zastaralé.  
  
## <a name="see-also"></a>Viz také  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
