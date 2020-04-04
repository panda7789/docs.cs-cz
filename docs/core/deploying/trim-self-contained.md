---
title: Oříznutí samostatných aplikací
description: Přečtěte si, jak oříznout samostatné aplikace, aby se zmenšila jejich velikost. .NET Core sdružuje runtime s aplikací, která je publikována samostatně a obecně obsahuje více runtime pak je nezbytné.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665633"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Oříznutí samostatných nasazení a spustitelných souborů

Při publikování samostatné aplikace je runtime .NET Core dodáván společně s aplikací. Toto sdružování přidá značné množství obsahu do vaší balené aplikace.

Pokud jde o nasazení aplikace, velikost je často důležitým faktorem. Zachování velikosti aplikace balíčku co nejmenší je obvykle cílem pro vývojáře aplikací.

V závislosti na složitosti aplikace je ke spuštění aplikace vyžadována pouze podmnožina runtime. Tyto nepoužívané části runtime jsou zbytečné a lze je oříznout z balené aplikace.

> [!NOTE]
> Oříznutí je experimentální funkce v rozhraní .NET Core 3.1 a je k dispozici _pouze_ pro aplikace, které jsou publikovány samostatně.

## <a name="trim-your-application"></a>Oříznutí aplikace

Následující příklad ukazuje, jak oříznout aplikaci pomocí příkazu [dotnet publish:](../tools/dotnet-publish.md)

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

Funkce oříznutí funguje tak, že zkoumá binární soubory aplikace, aby zjistila a vytvořila graf požadovaných sestav za běhu. Zbývající sestavení za běhu, na která se neodkazuje, jsou oříznuta.

## <a name="trimming-issues-when-using-reflection"></a>Problémy s oříznutím při použití odrazu

Existují scénáře, ve kterých funkce oříznutí se nezdaří rozpoznat odkazy. Například aplikace, která používá reflexe může spustit do tohoto problému, protože závislost na sestavení bude známa pouze v době běhu.

Oříznutí je pouze problém, pokud použití reflexe závisí na sestavení za běhu, který není odkazován přímo. Mějte na paměti, že kód aplikace nemusí používat reflexe přímo, ale sestavení jiného výrobce, na které odkazujete, jej může používat.

Když kód odkazuje na rozhraní API prostřednictvím reflexe a nechcete, aby propojovací program oříznout sestavení, které obsahuje toto rozhraní API, můžete upravit soubor projektu vyloučit sestavení z procesu oříznutí. Následující příklad ukazuje, jak zabránit `System.Security` oříznutí volaného sestavení:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a>Viz také

- [Nasazení aplikace .NET Core](index.md)
