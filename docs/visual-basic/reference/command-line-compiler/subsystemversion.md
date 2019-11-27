---
title: -subsystemversion
ms.date: 03/13/2018
helpviewer_keywords:
- /subsystemversion compiler option [Visual Basic]
- -subsystemversion compiler option [Visual Basic]
- subsystemversion compiler option [Visual Basic]
ms.assetid: 08be22b2-f447-4cd3-8203-120b1b920b54
ms.openlocfilehash: a977bc4cff822de551bf82d0f31707e9b2b6ea41
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348540"
---
# <a name="-subsystemversion-visual-basic"></a>-subsystemversion (Visual Basic)

Určuje minimální verzi subsystému, na kterém může být vygenerovaný spustitelný soubor spuštěn. tím se určí verze Windows, na kterých lze spustitelný soubor spustit. Nejčastěji tato možnost zajistí, že spustitelný soubor může využívat konkrétní funkce zabezpečení, které nejsou dostupné ve starších verzích Windows.

> [!NOTE]
> Chcete-li určit samotný podsystém, použijte možnost kompilátoru [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) .

## <a name="syntax"></a>Syntaxe

```vb
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
|Windows Server 2003|5.02|
|Windows Vista|6.00|
|Windows 7|6.01|
|Windows Server 2008|6.01|
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|

## <a name="default-values"></a>Výchozí hodnoty

Výchozí hodnota možnosti kompilátoru **-subsystemversion** závisí na podmínkách v následujícím seznamu:

- Výchozí hodnota je 6,02, pokud je nastavena možnost kompilátoru v následujícím seznamu:

  - [-target:appcontainerexe](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-target:winmdobj](../../../visual-basic/reference/command-line-compiler/target.md)

  - [-Platforma: ARM](../../../visual-basic/reference/command-line-compiler/platform.md)

- Výchozí hodnota je 6,00, pokud používáte MSBuild, cílíte .NET Framework 4,5 a nejste nastavili žádnou z možností kompilátoru, které byly zadány dříve v tomto seznamu.

- Výchozí hodnota je 4,00, pokud žádná z předchozích podmínek není pravdivá.

## <a name="setting-this-option"></a>Nastavení této možnosti

Chcete-li nastavit možnost kompilátoru **-subsystemversion** v sadě Visual Studio, je nutné otevřít soubor. vbproj a zadat hodnotu vlastnosti `SubsystemVersion` v souboru XML nástroje MSBuild. Tuto možnost nejde nastavit v integrovaném vývojovém prostředí (IDE) sady Visual Studio. Další informace naleznete v části "výchozí hodnoty" výše v tomto tématu nebo v tématu [běžné vlastnosti projektu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)

- [Vlastnosti nástroje MSBuild](/visualstudio/msbuild/msbuild-properties)
