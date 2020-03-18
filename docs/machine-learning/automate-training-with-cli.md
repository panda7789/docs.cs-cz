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
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="6e659-103">Automatizace tréninku modelu pomocí ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="6e659-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="6e659-104">Rozhraní ML.NET CLI automatizuje generování modelu pro vývojáře rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="6e659-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="6e659-105">Chcete-li použít ML.NET ROZHRANÍ API samo o sobě (bez ML.NET automatického rozhraní řízení podepisování ML.NET) musíte zvolit trenažér (implementace algoritmu strojového učení pro konkrétní úkol) a sadu transformací dat (funkce inženýrství) použít pro vaše data.</span><span class="sxs-lookup"><span data-stu-id="6e659-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="6e659-106">Optimální kanál se bude lišit pro každou datovou sadu a výběr optimální algoritmus ze všech možností zvyšuje složitost.</span><span class="sxs-lookup"><span data-stu-id="6e659-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="6e659-107">Ještě dále každý algoritmus má sadu hyperparameters, které mají být naladěny.</span><span class="sxs-lookup"><span data-stu-id="6e659-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="6e659-108">Proto můžete strávit týdny a někdy měsíce optimalizace modelu strojového učení se snaží najít nejlepší kombinace funkce inženýrství, učení algoritmy a hyperparametry.</span><span class="sxs-lookup"><span data-stu-id="6e659-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="6e659-109">ClI ML.NET zjednodušuje tento proces pomocí automatizovaného strojového učení (AutoML).</span><span class="sxs-lookup"><span data-stu-id="6e659-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="6e659-110">Toto téma odkazuje na ML.NET **cli** a ML.NET **AutoML**, které jsou aktuálně ve verzi Preview, a materiál může být může být změnit.</span><span class="sxs-lookup"><span data-stu-id="6e659-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="6e659-111">Co je rozhraní příkazového řádku ML.NET (CLI)?</span><span class="sxs-lookup"><span data-stu-id="6e659-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="6e659-112">Rozhraní ML.NET CLI je [nástroj .NET Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6e659-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="6e659-113">Po instalaci, můžete dát úlohu strojového učení a trénovací datové sady a generuje ML.NET model, stejně jako kód C# spustit pro použití modelu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6e659-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="6e659-114">Jak je znázorněno na následujícím obrázku, je jednoduché generovat vysoce kvalitní ML.NET modelu (serializovaný model .zip soubor) plus ukázkový kód C# pro spuštění/skóre tohoto modelu.</span><span class="sxs-lookup"><span data-stu-id="6e659-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="6e659-115">Kromě toho je také generován kód Jazyka C# pro vytvoření a trénování tohoto modelu, takže můžete zkoumat a iterovat algoritmus a nastavení použitá pro tento generovaný "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="6e659-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="6e659-116">![Obrázek](media/automate-training-with-cli/cli-high-level-process.png "Motor AutoML pracující uvnitř ML.NET CLI")</span><span class="sxs-lookup"><span data-stu-id="6e659-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="6e659-117">Tyto datové zdroje můžete generovat z vlastních datových sad bez vlastního kódování sami, takže také zvyšuje vaši produktivitu, i když již znáte ML.NET.</span><span class="sxs-lookup"><span data-stu-id="6e659-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="6e659-118">V současné době jsou úkoly ML podporované ML.NET cli:</span><span class="sxs-lookup"><span data-stu-id="6e659-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="6e659-119">Budoucnost: další úkoly `recommendation`strojového učení, jako jsou , `ranking`, `anomaly-detection`,`clustering`</span><span class="sxs-lookup"><span data-stu-id="6e659-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="6e659-120">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="6e659-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="6e659-122">Můžete jej spustit stejným způsobem na *Windows PowerShell*, \* macOS / Linux bash, nebo *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="6e659-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="6e659-123">Automatické dokončování tabulkových (návrhy parametrů) však nebude v *systému Windows CMD*fungovat .</span><span class="sxs-lookup"><span data-stu-id="6e659-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="6e659-124">Vytvořená výstupní aktiva</span><span class="sxs-lookup"><span data-stu-id="6e659-124">Output assets generated</span></span>

<span data-ttu-id="6e659-125">`auto-train` Příkaz PŘÍKAZ K PŘÍKAZU generuje ve výstupní složce následující datové zdroje:</span><span class="sxs-lookup"><span data-stu-id="6e659-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="6e659-126">Serializovaný model .zip ("nejlepší model") připravený k použití pro spuštění předpovědi.</span><span class="sxs-lookup"><span data-stu-id="6e659-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="6e659-127">Řešení Jazyka C# s:</span><span class="sxs-lookup"><span data-stu-id="6e659-127">C# solution with:</span></span>
  - <span data-ttu-id="6e659-128">C# kód pro spuštění/skóre, které generované model (chcete-li předpovědi v aplikacích koncových uživatelů s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="6e659-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="6e659-129">C# kód s trénovací kód slouží ke generování tohoto modelu (pro účely učení nebo přeškolení modelu).</span><span class="sxs-lookup"><span data-stu-id="6e659-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="6e659-130">Soubor protokolu s informacemi o všech iterací/sweeps přes více algoritmů vyhodnoceny, včetně jejich podrobnou konfiguraci/potrubí.</span><span class="sxs-lookup"><span data-stu-id="6e659-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="6e659-131">První dva datové zdroje lze přímo použít ve vašich aplikacích pro koncové uživatele (ASP.NET webové aplikace Core, služeb, desktopových aplikací atd.) k vytváření předpovědí s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="6e659-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="6e659-132">Třetí prostředek, trénovací kód, vám ukáže, jaký ML.NET kód rozhraní API byl použit rozhraním API k trénování generovaného modelu, takže můžete přeškolit model a prozkoumat a iterovat, na kterém konkrétní trenér/algoritmus a hyperparametry byly vybrány CLI a AutoML pod kryty.</span><span class="sxs-lookup"><span data-stu-id="6e659-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="6e659-133">Pochopení kvality modelu</span><span class="sxs-lookup"><span data-stu-id="6e659-133">Understanding the quality of the model</span></span>

<span data-ttu-id="6e659-134">Když pomocí nástroje cli vygenerujete "nejlepší model", zobrazí se metriky kvality (například přesnost a r-kvadrát) podle úkolu ML, na který cílíte.</span><span class="sxs-lookup"><span data-stu-id="6e659-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="6e659-135">Zde jsou tyto metriky shrnuty seskupeny podle úkolu ML, takže můžete pochopit kvalitu automaticky generovaného "nejlepšího modelu".</span><span class="sxs-lookup"><span data-stu-id="6e659-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="6e659-136">Metriky pro binární klasifikační modely</span><span class="sxs-lookup"><span data-stu-id="6e659-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="6e659-137">Následující seznam metrik úloh ml binární klasifikace pro prvních pět modelů nalezených v příkazovém příkazu příkazového příkazu:</span><span class="sxs-lookup"><span data-stu-id="6e659-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="6e659-139">Přesnost je oblíbenou metrikou pro problémy s klasifikací, ale přesnost není vždy nejlepší metrikou pro výběr nejlepšího modelu, jak je vysvětleno v následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="6e659-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="6e659-140">Existují případy, kdy je třeba vyhodnotit kvalitu modelu pomocí dalších metrik.</span><span class="sxs-lookup"><span data-stu-id="6e659-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="6e659-141">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, naleznete [v tématu vyhodnocení metriky pro binární klasifikace](resources/metrics.md#evaluation-metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="6e659-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="6e659-142">Metriky pro vícetřídní klasifikační modely</span><span class="sxs-lookup"><span data-stu-id="6e659-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="6e659-143">V následujícím textu se zobrazí seznam metrik úkolů ml klasifikace více tříd pro prvních pět modelů nalezených v příkazovém příkazu k řazení:</span><span class="sxs-lookup"><span data-stu-id="6e659-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="6e659-145">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, naleznete [v tématu vyhodnocení metriky pro vícetřídní klasifikace](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="6e659-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="6e659-146">Metriky pro regresní a doporučení modely</span><span class="sxs-lookup"><span data-stu-id="6e659-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="6e659-147">Regresní model dobře odpovídá datům, pokud jsou rozdíly mezi pozorovanými hodnotami a předpovídaných hodnotami modelu malé a nezaujaté.</span><span class="sxs-lookup"><span data-stu-id="6e659-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="6e659-148">Regrese lze vyhodnotit s určitými metrikami.</span><span class="sxs-lookup"><span data-stu-id="6e659-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="6e659-149">Zobrazí se podobný seznam metrik pro pět nejlepších modelů kvality, které najdete v zaokrenském systému.</span><span class="sxs-lookup"><span data-stu-id="6e659-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="6e659-150">V tomto konkrétním případě souvisejícím s regresní úlohou ML:</span><span class="sxs-lookup"><span data-stu-id="6e659-150">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="6e659-152">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem cli, najdete [v tématu vyhodnocení metriky pro regresi](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="6e659-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e659-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e659-153">See also</span></span>

- [<span data-ttu-id="6e659-154">Jak nainstalovat nástroj ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="6e659-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="6e659-155">Kurz: Analýza mínění pomocí ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="6e659-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="6e659-156">odkaz příkazu ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="6e659-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="6e659-157">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="6e659-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
