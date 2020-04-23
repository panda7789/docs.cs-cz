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
ms.openlocfilehash: c7d85222f35a61154e3eec70d8c9dad2ca6a32f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119856"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Postupy: Odebrání sestavení z globální mezipaměti sestavení

Existují dva způsoby, jak odebrat sestavení z globální mezipaměti sestavení (GAC):

- Pomocí [nástroje Global Assembly Cache (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md). Tuto možnost můžete použít k odinstalování sestavení, která jste umístili do GAC během vývoje a testování.

- Pomocí [Instalační služba systému Windows](/windows/desktop/Msi/windows-installer-portal). Tuto možnost byste měli použít k odinstalování sestavení při testování instalačních balíčků a pro produkční systémy.

## <a name="removing-an-assembly-with-gacutilexe"></a>Odebrání sestavení pomocí Gacutil. exe

Do příkazového řádku zadejte následující příkaz:

*název sestavení* pro **Gacutil – u** \<>

V tomto příkazu je *název sestavení* název sestavení, které chcete odebrat z globální mezipaměti sestavení (GAC).

> [!WARNING]
> Nástroj Gacutil. exe by neměl být použit k odebrání sestavení v produkčních systémech z důvodu možnosti, že sestavení může být stále vyžadováno určitou aplikací. Místo toho byste měli použít Instalační služba systému Windows, které udržují počet odkazů pro každé sestavení, které je nainstalováno v globální mezipaměti sestavení (GAC).

Následující příklad odebere sestavení s názvem `hello.dll` z globální mezipaměti sestavení (GAC):

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a>Odebrání sestavení pomocí Instalační služba systému Windows

V aplikaci **a funkce** v **Ovládacích panelech**vyberte aplikaci, kterou chcete odinstalovat. Pokud instalační balíček umístil sestavení do globální mezipaměti sestavení (GAC), Instalační služba systému Windows je odebere, pokud nejsou používány jinou aplikací.

> [!NOTE]
> Instalační služba systému Windows udržuje počet odkazů pro sestavení nainstalovaná v globální mezipaměti sestavení (GAC). Sestavení je odebráno z GAC pouze v případě, že počet odkazů dosáhne nuly, což znamená, že není používáno žádnou aplikací nainstalovanou Instalační služba systému Windows balíčkem.

## <a name="see-also"></a>Viz také

- [Práce se sestaveními a s globální pamětí sestavení](working-with-assemblies-and-the-gac.md)
- [Postupy: Instalace sestavení do globální mezipaměti sestavení](install-assembly-into-gac.md)
- [Gacutil. exe (nástroj Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md)
