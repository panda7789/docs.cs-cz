---
title: 'Postupy: Odebrání sestavení z globální mezipaměti sestavení'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c5f47f4c33f725377281146bef0a37dbd3f774c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753726"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Postupy: Odebrání sestavení z globální mezipaměti sestavení
Existují dva způsoby, jak odebrání sestavení z globální mezipaměti sestavení (GAC):  
  
-   Pomocí [nástroj globální mezipaměti sestavení (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Tato možnost slouží k odinstalaci sestavení, které jste umístili do mezipaměti GAC během vývoje a testování.  
  
-   Pomocí [Instalační služby systému Windows](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx). Tuto možnost používejte Odinstalace sestavení při testování instalační balíčky a pro produkční systémy.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Odebrání sestavení s Gacutil.exe  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil – u** \< *název sestavení*>  
  
     V tomto příkazu *název sestavení* je název sestavení pro odebrání z globální mezipaměti sestavení.  
  
    > [!WARNING]
    >  Neměli byste používat Gacutil.exe odebrat z důvodu možnost, že sestavení může stále nutné některé aplikace sestavení na produkční systémy. Místo toho používejte Instalační služby systému Windows, který udržuje počet odkazů pro každé sestavení, kdy se instaluje v mezipaměti GAC.  
  
 Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Odebrání sestavení s Instalační služby systému Windows  
  
1.  Z **programy a funkce** aplikace v **ovládací panely**, vyberte aplikaci, kterou chcete odinstalovat. Pokud se instalační balíček umístit sestavení v mezipaměti GAC, instalační služba systému Windows, budou odebrány Pokud nejsou použity v jiné aplikaci.  
  
    > [!NOTE]
    >  Instalační služba systému Windows udržuje počet odkazů pro sestavení, které jsou nainstalované v mezipaměti GAC. Sestavení se odebere z mezipaměti GAC jenom v případě, že jeho počet odkazů hodnota nula, který označuje, že není používán žádnou aplikaci nainstalovat balíček Instalační služby systému Windows.  
  
## <a name="see-also"></a>Viz také  
 [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
