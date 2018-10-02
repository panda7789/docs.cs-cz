---
title: Usnadnění ladění v rozhraní .NET bitovou kopii
description: Zjistěte, jak nakonfigurovat spustitelnou bitovou kopii pro snazší ladění pomocí integrovaného vývojového prostředí přepínače a možnosti příkazového řádku.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f25eaaa17d4c4bd2e9522591bb0fd66445cdb6f
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036023"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Usnadnění ladění v rozhraní .NET bitovou kopii

Při kompilaci nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Například můžete použít /**Zi** možnost příkazového řádku v jazyce Visual C++ klást na souborů ladění symbolů (přípona souboru .pdb). Podobně /**Od** možnost příkazového řádku instruuje kompilátor, aby zakáže optimalizaci. Výsledný kód pracuje pomaleji, ale je snazší ladit, musí to být nutné.

Při kompilaci rozhraní .NET Framework spravovaného kódu, kompilovat kompilátory jazyků jako Visual C++, Visual Basic a C# vlastní zdrojové programy do jazyka Microsoft intermediate language (MSIL). Jazyk MSIL je následně zkompilovaný pomocí kompilátoru JIT, těsně před spuštěním do nativního strojového kódu. Stejně jako u nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Můžete také nakonfigurovat JIT kompilaci pro ladění v podstatě stejným způsobem.

Tato konfigurace JIT má dva aspekty:

- Můžete požádat o JIT kompilátoru generování informací o sledování. To umožňuje ladicímu programu nalézt shodu se svým protějškem strojového kódu řetězce jazyka MSIL a sledovat, kde jsou uloženy místní proměnné a argumenty funkce. Od verze rozhraní .NET Framework verze 2.0, kompilátor JIT vždy generovat informace o sledování, takže není nutné o ně žádat.

- Můžete požádat o kompilátor JIT, aby neprováděl optimalizaci výsledného strojového kódu.

Za normálních okolností kompilátor, který generuje jazyk MSIL nastaví tyto možnosti kompilátoru JIT vhodným způsobem, na základě přepínačů IDE nebo parametrů příkazového řádku zadáte, například /**Od**.

V některých případech bude zapotřebí změnit chování kompilátoru JIT tak, aby bylo možné strojový kód, který generuje, snadněji ladit. Například může být třeba generovat informace o sledování JIT pro sestavení prodejní verze nebo pro optimalizaci řízení. To lze provést pomocí inicializačního souboru (.ini).

Například, pokud sestavení, který chcete ladit nazývá *MyApp.exe*, můžete vytvořit textový soubor s názvem *MyApp.ini*, ve stejné složce jako *MyApp.exe*, které obsahuje Tyto tři řádky:

```txt
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Hodnotu každé možnosti lze nastavit na 0 nebo 1 a chybějící možnost bude mít výchozí hodnotu 0. Nastavení volby `GenerateTrackingInfo` na hodnotu 1 a volby `AllowOptimize` na hodnotu 0 poskytuje nejjednodušší ladění.

Od verze rozhraní .NET Framework verze 2.0, kompilátor JIT vždy generovat informace o sledování bez ohledu na hodnotu pro `GenerateTrackingInfo`, nicméně `AllowOptimize` hodnota stále má vliv. Při použití [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) předkompilování nativní bitové kopie bez optimalizace, musí být k dispozici v cílové složce s souboru INI `AllowOptimize=0` při Ngen.exe spustí. Pokud máte předkompilovaných sestavení bez optimalizace, je nutné odebrat předkompilovaný kód pomocí NGen.exe **/ uninstall** možnost před opětovným spuštěním Ngen.exe předkompilování kódu jako optimalizovaného. Pokud není k dispozici ve složce soubor .ini, Ngen.exe předkompilování kódu jako optimalizovaného.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> určuje nastavení sestavení. **DebuggableAttribute** obsahuje dvě pole určující, zda kompilátor JIT by měl optimalizaci a/nebo generovat informace o sledování. Od verze rozhraní .NET Framework verze 2.0, kompilátor JIT vždy generovat informace o sledování.

Pro sestavení prodejní verze, kompilátory nemají nastavený žádný **DebuggableAttribute**. Ve výchozím nastavení vygeneruje kompilátor JIT nejvyšší výkon s nejtěžší možností ladění strojového kódu. Povolením JIT sledování se snižuje výkon a vypnutím optimalizace se výkon razantně snižuje.

**DebuggableAttribute** se vztahuje na celé sestavení najednou, nikoli na jednotlivé moduly v rámci sestavení. Nástroje pro vývoj proto musí připojit vlastní atributy k tokenu metadat sestavení, pokud sestavení má již byl vytvořen, nebo ke třídě s názvem **System.Runtime.CompilerServices.AssemblyAttributesGoHere**. Nástroj ALink následně podporuje tyto **DebuggableAttribute** atributy z každého modulu na sestavení stanou součástí. Pokud dojde ke konfliktu, operace nástroje ALink se nezdaří.

> [!NOTE]
> V rozhraní .NET Framework verze 1.0, přidá kompilátor jazyka Microsoft Visual C++ **DebuggableAttribute** při **/CLR** a **/zi** jsou zadány možnosti kompilátoru. Ve verzi 1.1 rozhraní .NET Framework, musíte buď přidat **DebugabbleAttribute** ručně v kódu nebo použití **/assemblydebug** – možnost linkeru.

## <a name="see-also"></a>Viz také:

- [Ladění, trasování a profilace](../../../docs/framework/debug-trace-profile/index.md)
- [Povolení JIT – ladění Attach](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)
- [Povolení profilace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
