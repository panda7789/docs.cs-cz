---
title: Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET
description: Zjistěte, jak pomocí nástroje CLI ML.NET automaticky proškolit nejlepší model z příkazového řádku.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: d7c6102c2257be1daa613fde0edabce83d04b414
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589656"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET

ML.NET CLI automatizuje generování modelů pro vývojáře v rozhraní .NET.

Pokud chcete používat rozhraní ML.NET API samostatně, (bez ML.NET AutoML CLI), musíte zvolit Trainer (implementaci algoritmu strojového učení pro konkrétní úlohu) a sadu transformací dat (metodologie funkcí), která se použije na vaše data. Optimální kanál se bude pro každou datovou sadu lišit a výběr optimálního algoritmu ze všech voleb zvyšuje složitost. Ještě více, každý algoritmus má sadu parametrů, které se mají vyladit. Proto můžete strávit týdny a někdy měsíce na optimalizaci modelů ve službě Machine Learning, které se snaží najít nejlepší kombinace funkcí pro inženýry, výukové algoritmy a základní parametry.

ML.NET CLI tento proces zjednodušuje pomocí automatizovaného strojového učení (AutoML).

> [!NOTE]
> Toto téma odkazuje na ML.NET **CLI** a ml.NET **AutoML**, které jsou momentálně ve verzi Preview, a materiál může být změněn.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co je rozhraní příkazového řádku ML.NET (CLI)?

ML.NET CLI je [nástroj .NET Core](../core/tools/global-tools.md). Po nainstalování mu udělíte úlohu strojového učení a školicí datovou sadu, která generuje ML.NET model a také kód jazyka C#, který se má spustit pro použití modelu ve vaší aplikaci.

Jak je znázorněno na následujícím obrázku, je jednoduché vytvořit vysoce kvalitní ML.NET model (soubor s serializovaným modelem. zip) a ukázkový kód jazyka C# pro spuštění nebo určení skóre modelu. Kromě toho se generuje kód C# pro vytvoření nebo výuku modelu, takže můžete prozkoumat a iterovat algoritmus a nastavení použitá pro vygenerovaný "nejlepší model".

![obrazu](media/automate-training-with-cli/cli-high-level-process.png "AutoML Engine pracuje v rozhraní příkazového řádku ML.NET")

Tyto prostředky můžete vygenerovat z vlastních datových sad, aniž byste je museli kódovat sami, takže také zlepší vaši produktivitu, i když už znáte ML.NET.

V současné době jsou úlohy ML podporované rozhraním příkazového řádku ML.NET:

- klasifikace (binární a více tříd)
- nevýhody
- základě
- Budoucí: další úlohy strojového učení, jako je například klasifikace imagí, hodnocení, detekce anomálií, clusteringu

Příklad použití (klasifikační scénář):

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image](media/automate-training-with-cli/mlnet-classification-powershell.gif)

Můžete ho spustit stejným způsobem jako v *prostředí Windows PowerShell*, *MacOS/Linux bash*nebo *Windows CMD*. Automatické dokončování v tabulkovém prostředí (návrhy parametrů) ale nebude fungovat ve *Windows CMD*.

## <a name="output-assets-generated"></a>Vygenerované výstupní prostředky

Příkazy úkolu ML v rozhraní příkazového řádku generují následující prostředky ve výstupní složce:

- Serializovaný model. zip ("nejlepší model") je připravený k použití ke spuštění předpovědi.
- Řešení C# s:
  - Kód jazyka C# ke spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).
  - Kód jazyka C# s školicím kódem, který slouží ke generování tohoto modelu (pro účely učení nebo přeškolení modelu).
- Soubor protokolu s informacemi o všech iteracích/rozcyklcích v rámci více vyhodnocených algoritmů, včetně jejich podrobné konfigurace/kanálu.

První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.) k tomu, aby se předpovědi s tímto generovaným modelem ML.

Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete přesměrovat svůj model a prozkoumat a iterovat na to, které konkrétní Trainer/algoritmus a parametry byly vybrány rozhraním CLI a AutoML v rámci pokrývání.

## <a name="understanding-the-quality-of-the-model"></a>Princip kvality modelu

Když vygenerujete "nejlepší model" pomocí nástroje CLI, uvidíte metriky kvality (například přesnost a R-kvadrát) podle potřeby pro úlohu ML, na kterou cílíte.

Tady jsou tyto metriky shrnuté podle úkolu ML, abyste porozuměli kvalitě automaticky generovaného nejlepšího modelu.

### <a name="metrics-for-classification-models"></a>Metriky pro modely klasifikace

V následujícím seznamu se zobrazí seznam metrik klasifikace pro nejoblíbenější pět modelů nalezené rozhraním příkazového řádku:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 Přesnost je oblíbená metrika pro problémy s klasifikací, ale přesnost není vždy nejlepší metrikou pro výběr nejlepšího modelu, jak je vysvětleno v následujících odkazech. Existují případy, kdy potřebujete vyhodnotit kvalitu modelu s dalšími metrikami.

Pro zkoumání a pochopení metrik, které jsou výstupem rozhraní příkazového řádku, si přečtěte [metriky vyhodnocení pro klasifikaci](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Metriky pro regrese a modely doporučení

Regresní model odpovídá datům, pokud jsou rozdíly mezi zjištěnými hodnotami a předpovězenými hodnotami modelu malé a neposunuté. Regresi je možné vyhodnotit pomocí určitých metrik.

Zobrazí se podobný seznam metrik pro nejlépe pět modelů kvality, které rozhraní příkazového řádku najde. V tomto konkrétním případě, který se týká úlohy regresní ML:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Chcete-li prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku, přečtěte si téma [vyhodnocení metrik pro regresi](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Viz také

- [Postup instalace nástroje ML.NET CLI](how-to-guides/install-ml-net-cli.md)
- [Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET](tutorials/sentiment-analysis-cli.md)
- [Reference k příkazům rozhraní příkazového řádku ML.NET](reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](resources/ml-net-cli-telemetry.md)
