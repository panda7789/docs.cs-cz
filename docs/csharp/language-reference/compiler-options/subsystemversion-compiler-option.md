---
title: -subsystemversion (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802041"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (Možnosti kompilátoru Jazyka C#)

Určuje minimální verzi subsystému, ve kterém může být spuštěn generovaný spustitelný soubor, čímž určí verze systému Windows, ve kterých lze spustit spustitelný soubor. Tato možnost nejčastěji zajišťuje, že spustitelný soubor může využívat určité funkce zabezpečení, které nejsou k dispozici ve starších verzích systému Windows.

> [!NOTE]
> Chcete-li určit samotný subsystém, použijte možnost kompilátoru [-target.](./target-compiler-option.md)

## <a name="syntax"></a>Syntaxe

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametry

`major.minor`

Minimální požadovaná verze subsystému vyjádřená v zápisu dot pro hlavní a dílčí verze. Můžete například určit, že aplikace nemůže být spuštěna v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6.01, jak popisuje tabulka dále v tomto tématu. Je nutné zadat `major` hodnoty `minor` pro a jako celá čísla.

Úvodní nuly `minor` ve verzi nemění verzi, ale koncové nuly ano. Například 6.1 a 6.01 odkazují na stejnou verzi, ale 6.10 odkazuje na jinou verzi. Doporučujeme vyjádřit dílčí verzi jako dvě číslice, aby nedošlo k záměně.

## <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny běžné verze systému Windows pro podsystém.

|Verze systému Windows|Verze subsystému|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Výchozí hodnoty

Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:

- Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:

  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [-target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-platforma:rameno](./platform-compiler-option.md)

- Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte na rozhraní .NET Framework 4.5 a nenastavili jste žádné možnosti kompilátoru, které byly zadány dříve v tomto seznamu.

- Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek je true.

## <a name="setting-this-option"></a>Nastavení této možnosti

Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, musíte `SubsystemVersion` otevřít soubor .csproj a zadat hodnotu vlastnosti v xml MSBuild. Tuto možnost nelze nastavit v ide sady Visual Studio. Další informace naleznete v tématu "Výchozí hodnoty" dříve v tomto tématu nebo [společné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
