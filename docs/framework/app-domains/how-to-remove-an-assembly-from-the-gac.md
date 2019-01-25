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
ms.openlocfilehash: 4a8077125ac99fa1d8f5b22ac3864fcc17213fa6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639628"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Postupy: Odebrání sestavení z globální mezipaměti sestavení
Existují dva způsoby, jak odebrání sestavení z globální mezipaměti sestavení (GAC):  
  
-   S použitím [nástroj Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md). Tuto možnost můžete použít k odinstalování sestavení, které jste umístili do mezipaměti GAC během vývoje a testování.  
  
-   S použitím [Instalační služby systému Windows](/windows/desktop/Msi/windows-installer-portal). Tuto možnost používejte k odinstalování sestavení při testování instalační balíčky a pro produkční systémy.  
  
### <a name="removing-an-assembly-with-gacutilexe"></a>Odebrání sestavení s Gacutil.exe  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     **Gacutil – u** \< *název sestavení*>  
  
     V tomto příkazu *název sestavení* je název sestavení z globální mezipaměti sestavení odebrat.  
  
    > [!WARNING]
    >  Neměli byste používat Gacutil.exe odebrat sestavení na produkční systémy z důvodu možnost, že sestavení můžou stále vyžadovat některé aplikace. Místo toho by měl použít instalační program Windows, který udržuje počet odkazů pro každé sestavení, kdy se instaluje v mezipaměti GAC.  
  
 Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení.  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a>Odebrání sestavení pomocí Instalační služby systému Windows  
  
1.  Z **programy a funkce** aplikace v **ovládací panely**, vyberte aplikaci, kterou chcete odinstalovat. Pokud instalační balíček umístí sestavení v mezipaměti GAC, instalační služby systému Windows, budou odebrány Pokud nejsou použity v jiné aplikaci.  
  
    > [!NOTE]
    >  Instalační program Windows udržuje počet odkazů pro sestavení nainstalovaná v GAC. Sestavení se odebere z mezipaměti GAC, pouze v případě, že jeho počet odkazů dosáhne nuly, což znamená, že není použit ve všech aplikacích nainstalovat balíček Instalační služby systému Windows.  
  
## <a name="see-also"></a>Viz také:
- [Práce se sestaveními a s globální pamětí sestavení](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Postupy: Instalace sestavení do globální mezipaměti sestavení](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)
- [Gacutil.exe (nástroj globální mezipaměti sestavení)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
