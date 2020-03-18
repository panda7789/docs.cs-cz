---
title: Automatizace tréninku modelu pomocí ML.NET CLI
description: Zjistěte, jak pomocí nástroje ML.NET CLI automaticky trénovat nejlepší model z příkazového řádku.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185886"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatizace tréninku modelu pomocí ML.NET CLI

Rozhraní ML.NET CLI automatizuje generování modelu pro vývojáře rozhraní .NET.

Chcete-li použít ML.NET ROZHRANÍ API samo o sobě (bez ML.NET automatického rozhraní řízení podepisování ML.NET) musíte zvolit trenažér (implementace algoritmu strojového učení pro konkrétní úkol) a sadu transformací dat (funkce inženýrství) použít pro vaše data. Optimální kanál se bude lišit pro každou datovou sadu a výběr optimální algoritmus ze všech možností zvyšuje složitost. Ještě dále každý algoritmus má sadu hyperparameters, které mají být naladěny. Proto můžete strávit týdny a někdy měsíce optimalizace modelu strojového učení se snaží najít nejlepší kombinace funkce inženýrství, učení algoritmy a hyperparametry.

ClI ML.NET zjednodušuje tento proces pomocí automatizovaného strojového učení (AutoML).

> [!NOTE]
> Toto téma odkazuje na ML.NET **cli** a ML.NET **AutoML**, které jsou aktuálně ve verzi Preview, a materiál může být může být změnit.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co je rozhraní příkazového řádku ML.NET (CLI)?

Rozhraní ML.NET CLI je [nástroj .NET Core](../core/tools/global-tools.md). Po instalaci, můžete dát úlohu strojového učení a trénovací datové sady a generuje ML.NET model, stejně jako kód C# spustit pro použití modelu ve vaší aplikaci.

Jak je znázorněno na následujícím obrázku, je jednoduché generovat vysoce kvalitní ML.NET modelu (serializovaný model .zip soubor) plus ukázkový kód C# pro spuštění/skóre tohoto modelu. Kromě toho je také generován kód Jazyka C# pro vytvoření a trénování tohoto modelu, takže můžete zkoumat a iterovat algoritmus a nastavení použitá pro tento generovaný "nejlepší model".

![Obrázek](media/automate-training-with-cli/cli-high-level-process.png "Motor AutoML pracující uvnitř ML.NET CLI")

Tyto datové zdroje můžete generovat z vlastních datových sad bez vlastního kódování sami, takže také zvyšuje vaši produktivitu, i když již znáte ML.NET.

V současné době jsou úkoly ML podporované ML.NET cli:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Budoucnost: další úkoly `recommendation`strojového učení, jako jsou , `ranking`, `anomaly-detection`,`clustering`

Příklad použití:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

Můžete jej spustit stejným způsobem na *Windows PowerShell*, * macOS / Linux bash, nebo *Windows CMD*. Automatické dokončování tabulkových (návrhy parametrů) však nebude v *systému Windows CMD*fungovat .

## <a name="output-assets-generated"></a>Vytvořená výstupní aktiva

`auto-train` Příkaz PŘÍKAZ K PŘÍKAZU generuje ve výstupní složce následující datové zdroje:

- Serializovaný model .zip ("nejlepší model") připravený k použití pro spuštění předpovědi.
- Řešení Jazyka C# s:
  - C# kód pro spuštění/skóre, které generované model (chcete-li předpovědi v aplikacích koncových uživatelů s tímto modelem).
  - C# kód s trénovací kód slouží ke generování tohoto modelu (pro účely učení nebo přeškolení modelu).
- Soubor protokolu s informacemi o všech iterací/sweeps přes více algoritmů vyhodnoceny, včetně jejich podrobnou konfiguraci/potrubí.

První dva datové zdroje lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET webové aplikace Core, služeb, desktopových aplikací atd.) k vytváření předpovědí s tímto generovaným modelem ML.

Třetí prostředek, trénovací kód, vám ukáže, jaký ML.NET kód rozhraní API byl použit rozhraním API k trénování generovaného modelu, takže můžete přeškolit model a prozkoumat a iterovat, na kterém konkrétní trenér/algoritmus a hyperparametry byly vybrány CLI a AutoML pod kryty.

## <a name="understanding-the-quality-of-the-model"></a>Pochopení kvality modelu

Když pomocí nástroje cli vygenerujete "nejlepší model", zobrazí se metriky kvality (například přesnost a r-kvadrát) podle úkolu ML, na který cílíte.

Zde jsou tyto metriky shrnuty seskupeny podle úkolu ML, takže můžete pochopit kvalitu automaticky generovaného "nejlepšího modelu".

### <a name="metrics-for-binary-classification-models"></a>Metriky pro binární klasifikační modely

Následující seznam metrik úloh ml binární klasifikace pro prvních pět modelů nalezených v příkazovém příkazu příkazového příkazu:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Přesnost je oblíbenou metrikou pro problémy s klasifikací, ale přesnost není vždy nejlepší metrikou pro výběr nejlepšího modelu, jak je vysvětleno v následujících odkazech. Existují případy, kdy je třeba vyhodnotit kvalitu modelu pomocí dalších metrik.

Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, naleznete [v tématu vyhodnocení metriky pro binární klasifikace](resources/metrics.md#evaluation-metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Metriky pro vícetřídní klasifikační modely

V následujícím textu se zobrazí seznam metrik úkolů ml klasifikace více tříd pro prvních pět modelů nalezených v příkazovém příkazu k řazení:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, naleznete [v tématu vyhodnocení metriky pro vícetřídní klasifikace](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Metriky pro regresní a doporučení modely

Regresní model dobře odpovídá datům, pokud jsou rozdíly mezi pozorovanými hodnotami a předpovídaných hodnotami modelu malé a nezaujaté. Regrese lze vyhodnotit s určitými metrikami.

Zobrazí se podobný seznam metrik pro pět nejlepších modelů kvality, které najdete v zaokrenském systému. V tomto konkrétním případě souvisejícím s regresní úlohou ML:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, najdete [v tématu vyhodnocení metriky pro regresi](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Viz také

- [Jak nainstalovat nástroj ML.NET CLI](how-to-guides/install-ml-net-cli.md)
- [Kurz: Analýza mínění pomocí ML.NET CLI](tutorials/sentiment-analysis-cli.md)
- [odkaz příkazu ML.NET CLI](reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](resources/ml-net-cli-telemetry.md)
