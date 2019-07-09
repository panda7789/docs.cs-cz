---
title: Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET
description: Objevte, jak pomocí nástroje příkazového řádku ML.NET automaticky trénování nejlepší model z příkazového řádku.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663929"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET

Rozhraní příkazového řádku ML.NET "demokratizuje" ML.NET pro vývojáře na platformě .NET při učení ML.NET.

K používání rozhraní API ML.NET samostatně, (bez rozhraní příkazového řádku AutoML ML.NET) musíte zvolit trainer (provádění algoritmu strojového učení pro určité úlohy) a sadu transformace dat (vytváření funkcí) použít k vašim datům. Optimální kanál se budou lišit pro každou datovou sadu a výběr optimálního algoritmu ze všech možností přidá na složitost. Ještě více jednotlivých algoritmus využívající dlaždice má sadu hyperparameters ladit. Proto můžete věnovat týdnů a někdy měsíců na strojového učení při hledání nejlepších kombinace vytváření funkcí, algoritmů učení a hyperparameters optimalizace modelu.

Tento proces je možné automatizovat pomocí rozhraní příkazového řádku ML.NET, která implementuje modul inteligentních ML.NET AutoML.

> [!NOTE]
> Toto téma odkazuje na ML.NET **rozhraní příkazového řádku** a ML.NET **AutoML**, které jsou aktuálně ve verzi Preview a materiálu se můžou stát terčem změnit.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co je ML.NET rozhraní příkazového řádku (CLI)?

Rozhraní příkazového řádku ML.NET můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) pro vytváření kvalitní ML.NET modely a zdrojový kód založený na trénovací datové sady.

Jak je znázorněno na následujícím obrázku, je to jednoduché ke generování modelu ML.NET vysoce kvalitní (serializovaný model soubor .zip) plus vzorku C# kód pro spuštění/určení skóre modelu. Kromě toho C# k vytvoření a trénování modelu také generování kódu, takže můžete prozkoumat a iterovat algoritmu a nastavení, která vygeneruje "nejlepší model".

![Obrázek](media/automate-training-with-cli/cli-high-level-process.png "AutoML modul práci uvnitř rozhraní příkazového řádku ML.NET")

Tyto prostředky můžete vygenerovat z vlastní datové sady bez kódování sami, tak i v případě, že již znáte ML.NET také zlepšuje produktivitu.

V současné době nepodporuje rozhraní příkazového řádku ML.NET úlohy ML jsou:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Budoucnost: jiných strojového učení s úkoly, jako `recommendation`, `ranking`, `anomaly-detection`, `clustering`

Příklad použití:

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![obrázek](media/automate-training-with-cli/cli-model-generation.gif)

Můžete ji spustit stejný způsobem on *prostředí Windows PowerShell*, * bash v systému macOS nebo Linux, nebo *Windows CMD*. Ale tabulkové automatického dokončování (parametr návrhy) nebudou fungovat ve *Windows CMD*.

## <a name="output-assets-generated"></a>Vygeneruje výstupní assety

Rozhraní příkazového řádku `auto-train` příkaz vytvoří následující prostředky ve výstupní složce:

- Serializovaný model soubor .zip ("nejlepší model") připravený k použití pro spouštěním predikcí.
- C#řešení:
  - C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).
  - C#kód s kódem školení sloužící ke generování tohoto modelu (pro výukové účely nebo přetrénování modelů).
- Soubor protokolu s informacemi o všech iterací/změny napříč několika algoritmů vyhodnotí, včetně jejich podrobné konfigurace/kanálu.

První dva prostředky lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovanou modelu ML.

Třetí asset školení kód ukazuje, můžete kód ML.NET API použil rozhraní příkazového řádku pro trénování modelu vygenerovaný, tak přeučování váš model, prozkoumat a iterovat na jaké konkrétní trainer/algoritmu a hyperparameters byly vybrány tak, že rozhraní příkazového řádku a AutoML pod pokličkou.

## <a name="understanding-the-quality-of-the-model"></a>Principy kvality tohoto modelu

Při generování "nejlepší model" pomocí nástroje příkazového řádku zobrazí metrik kvality (jako jsou správnost a spolehlivosti R) v závislosti na ML úkol, který cílíte.

Tady Shrneme informace z těchto metrik seskupené podle úlohy ML to vám umožní pochopit kvality vaší auto-generated "nejlepší model".

### <a name="metrics-for-binary-classification-models"></a>Metriky pro binární klasifikační modely

Následující seznam binární klasifikace ML úloh metrik pro hlavní pět modelů nalezené pomocí rozhraní příkazového řádku:

![obrázek](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Přesnost je Oblíbené metriky pro klasifikaci problémy, ale přesnost není vždy nejlepší metrika vybrat nejlepší model z jak je vysvětleno v odkazech níže. Existují případy, kdy potřebujete pro vyhodnocení kvality modelu pomocí další metriky.

Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro binární klasifikaci](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Metriky pro modelů klasifikace víc tříd

Následující zobrazí seznam klasifikací roc ML úloh metrik pro hlavní pět modelů nalezené pomocí rozhraní příkazového řádku:

![obrázek](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro klasifikace víc tříd](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Metriky pro regresní modely

Regresní model odpovídá zpracovávaným datům, pokud jsou rozdíly mezi zjištěnou hodnoty a modelu předpovězeným hodnotám malé a neposunutého. Regrese mohou být vyhodnoceny s určité metriky.

Zobrazí se podobná seznam metrik pro nejlepší nejvyšší kvality pět modelů nalezené pomocí rozhraní příkazového řádku. V tomto konkrétním případě související regrese ML úlohy:

![obrázek](media/automate-training-with-cli/cli-regression-metrics.png)

Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro regresní](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Viz také:

- [Postup instalace nástroje rozhraní příkazového řádku ML.NET](how-to-guides/install-ml-net-cli.md)
- [Kurz: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET](tutorials/mlnet-cli.md)
- [Reference k příkazům rozhraní příkazového řádku ML.NET](reference/ml-net-cli-reference.md)
- [Telemetrie v rozhraní příkazového řádku ML.NET](resources/ml-net-cli-telemetry.md)
