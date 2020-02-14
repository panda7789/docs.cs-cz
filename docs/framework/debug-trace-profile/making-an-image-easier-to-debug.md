---
title: Usnadnění ladění obrazu v .NET
description: Naučte se konfigurovat spustitelnou bitovou kopii pro snazší ladění pomocí přepínačů IDE a možností příkazového řádku.
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
ms.openlocfilehash: 44d512a8ebec0e21e33f51c07428331e5e22b7bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217331"
---
# <a name="making-an-image-easier-to-debug-in-net"></a>Usnadnění ladění obrazu v .NET

Při kompilaci nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Například můžete použít možnost příkazového řádku/**Zi** v vizuálu C++ a požádat ho, aby vygeneroval soubory se symboly ladění (Přípona souboru. pdb). Obdobně parametr příkazového řádku/**Oh** instruuje kompilátor, aby zakázal optimalizaci. Výsledný kód pracuje pomaleji, ale je možné jej snadno ladit, pokud je to nezbytné.

Při kompilování .NET Framework spravovaného kódu, kompilátory, C++jako je například Visual C# , Visual Basic a kompilování zdrojového programu do jazyka MSIL (Microsoft Intermediate Language). Jazyk MSIL je následně kompilován JIT těsně před provedením do nativního strojového kódu. Stejně jako u nespravovaného kódu je možné nakonfigurovat spustitelnou bitovou kopii pro ladění nastavením přepínačů IDE nebo parametrů příkazového řádku. Můžete také nakonfigurovat kompilaci JIT pro ladění v podstatě stejným způsobem.

Tato konfigurace JIT má dva aspekty:

- Můžete požádat kompilátor JIT, aby vygeneroval informace o sledování. To umožňuje ladicímu programu nalézt shodu se svým protějškem strojového kódu řetězce jazyka MSIL a sledovat, kde jsou uloženy místní proměnné a argumenty funkce. Počínaje verzí 2,0 .NET Framework kompilátor JIT vždy generuje informace o sledování, takže není nutné si je vyžádat.

- Můžete požádat kompilátor JIT, aby neoptimalizoval výsledný strojový kód.

Obvykle kompilátor, který generuje jazyk MSIL, nastavuje tyto možnosti kompilátoru JIT odpovídajícím způsobem na základě přepínačů IDE nebo parametrů příkazového řádku, které zadáte, například/**Oh**.

V některých případech bude zapotřebí změnit chování kompilátoru JIT tak, aby bylo možné strojový kód, který generuje, snadněji ladit. Například může být třeba generovat informace o sledování JIT pro sestavení prodejní verze nebo pro optimalizaci řízení. To lze provést pomocí inicializačního souboru (.ini).

Například pokud sestavení, které chcete ladit, se nazývá *MyApp. exe*, můžete vytvořit textový soubor s názvem *MyApp. ini*ve stejné složce jako *MyApp. exe*, který obsahuje tyto tři řádky:

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

Hodnotu každé možnosti lze nastavit na 0 nebo 1 a chybějící možnost bude mít výchozí hodnotu 0. Nastavení volby `GenerateTrackingInfo` na hodnotu 1 a volby `AllowOptimize` na hodnotu 0 poskytuje nejjednodušší ladění.

Počínaje verzí 2,0 .NET Framework kompilátor JIT vždy generuje informace o sledování bez ohledu na hodnotu pro `GenerateTrackingInfo`; Nicméně hodnota `AllowOptimize` má stále vliv. Při použití nástroje [Ngen. exe (generátor nativních bitových kopií)](../tools/ngen-exe-native-image-generator.md) k předkompilování nativní bitové kopie bez optimalizace musí být soubor. ini přítomen v cílové složce s `AllowOptimize=0`, když se spustí Ngen. exe. Pokud jste předkompilováni sestavení bez optimalizace, je nutné před opětovným spuštěním nástroje Ngen. exe, aby byl kód předem kompilován jako optimalizovaný, odebrat předkompilovaný kód pomocí možnosti NGen. exe **/Uninstall** . Pokud soubor. ini není ve složce přítomen, ve výchozím nastavení předkompiluje nástroj Ngen. exe kód jako optimalizovaný.

<xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> určuje nastavení sestavení. **DebuggableAttribute** obsahuje dvě pole, která určují, zda má kompilátor JIT optimalizovat a/nebo generovat informace o sledování. Počínaje verzí 2,0 .NET Framework kompilátor JIT vždy generuje informace o sledování.

Pro maloobchodní sestavení nejsou kompilátory nastaveny žádné **DebuggableAttribute**. Ve výchozím nastavení generuje kompilátor JIT nejvyšší výkon, který je nejzávažnější pro ladění strojového kódu. Povolením JIT sledování se snižuje výkon a vypnutím optimalizace se výkon razantně snižuje.

**DebuggableAttribute** se vztahuje na celé sestavení v čase, nikoli na jednotlivé moduly v rámci sestavení. Vývojové nástroje musí proto připojit vlastní atributy k tokenu metadat sestavení, pokud již bylo sestavení vytvořeno, nebo ke třídě s názvem **System. Runtime. CompilerServices. AssemblyAttributesGoHere**. Nástroj ALink pak propaguje tyto atributy **DebuggableAttribute** z každého modulu na sestavení, které se stane součástí. Pokud dojde ke konfliktu, operace ALink se nezdařila.

> [!NOTE]
> Ve verzi 1,0 .NET Framework C++ kompilátor Microsoft Visual Compiler přidá rozhraní **DebuggableAttribute** , pokud jsou zadány možnosti kompilátoru **/CLR** a **/Zi** . Ve verzi 1,1 .NET Framework musíte buď ručně přidat **DebuggableAttribute** do kódu, nebo použít možnost linkeru **/ASSEMBLYDEBUG** .

## <a name="see-also"></a>Viz také

- [Ladění, trasování a profilace](index.md)
- [Povolení JIT – ladění Attach](enabling-jit-attach-debugging.md)
- [Povolení profilace](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))
