---
title: -subsystemversion (C# možnosti kompilátoru)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: d76c9424340b4b6f3c211c849b466be55eb79d1e
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802041"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (C# možnosti kompilátoru)

Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit. Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.

> [!NOTE]
> Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](./target-compiler-option.md) .

## <a name="syntax"></a>Syntaxe

```console
-subsystemversion:major.minor
```

## <a name="parameters"></a>Parametry

`major.minor`

Minimální požadovaná verze subsystému, jak je vyjádřena v zápisu tečky pro hlavní a dílčí verze. Například můžete určit, že aplikace nemůže běžet v operačním systému, který je starší než Windows 7, pokud nastavíte hodnotu této možnosti na 6,01, jak je popsáno v tabulce dále v tomto tématu. Je nutné zadat hodnoty pro `major` a `minor` jako celá čísla.

Počáteční nuly ve verzi `minor` nemění verzi, ale mají na konci nula. Například 6,1 a 6,01 odkazují na stejnou verzi, ale 6,10 odkazuje na jinou verzi. Pokud chcete zabránit nejasnostem, doporučujeme, abyste podverze vyjádřili jako dvě číslice.

## <a name="remarks"></a>Poznámky

V následující tabulce jsou uvedeny běžné verze subsystému Windows.

|Verze systému Windows|Verze subsystému|
|---------------------|-----------------------|
|Windows 2000|5.00|
|Windows XP|5.01|
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|Windows 8|6.02|

## <a name="default-values"></a>Výchozí hodnoty

Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:

- Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:

  - [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)

  - [-target:winmdobj](./target-winmdobj-compiler-option.md)

  - [-Platforma: ARM](./platform-compiler-option.md)

- Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.

- Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.

## <a name="setting-this-option"></a>Nastavení této možnosti

Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. csproj a zadat hodnotu vlastnosti `SubsystemVersion` v souboru XML nástroje MSBuild. Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio. Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
