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
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="a7ce2-103">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="a7ce2-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="a7ce2-104">ML.NET CLI automatizuje generování modelů pro vývojáře v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="a7ce2-105">Pokud chcete používat rozhraní ML.NET API samostatně, (bez ML.NET AutoML CLI), musíte zvolit Trainer (implementaci algoritmu strojového učení pro konkrétní úlohu) a sadu transformací dat (metodologie funkcí), která se použije na vaše data.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="a7ce2-106">Optimální kanál se bude pro každou datovou sadu lišit a výběr optimálního algoritmu ze všech voleb zvyšuje složitost.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="a7ce2-107">Ještě více, každý algoritmus má sadu parametrů, které se mají vyladit.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="a7ce2-108">Proto můžete strávit týdny a někdy měsíce na optimalizaci modelů ve službě Machine Learning, které se snaží najít nejlepší kombinace funkcí pro inženýry, výukové algoritmy a základní parametry.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="a7ce2-109">ML.NET CLI tento proces zjednodušuje pomocí automatizovaného strojového učení (AutoML).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="a7ce2-110">Toto téma odkazuje na ML.NET **CLI** a ml.NET **AutoML**, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="a7ce2-111">Co je rozhraní příkazového řádku ML.NET (CLI)?</span><span class="sxs-lookup"><span data-stu-id="a7ce2-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="a7ce2-112">ML.NET CLI je [nástroj .NET Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="a7ce2-113">Po nainstalování mu udělíte úlohu strojového učení a školicí datovou sadu, která generuje ML.NET model a také kód jazyka C#, který se má spustit pro použití modelu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="a7ce2-114">Jak je znázorněno na následujícím obrázku, je jednoduché vytvořit vysoce kvalitní ML.NET model (soubor s serializovaným modelem. zip) a ukázkový kód jazyka C# pro spuštění nebo určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="a7ce2-115">Kromě toho se generuje kód C# pro vytvoření nebo výuku modelu, takže můžete prozkoumat a iterovat algoritmus a nastavení použitá pro vygenerovaný "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="a7ce2-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="a7ce2-116">![obrazu](media/automate-training-with-cli/cli-high-level-process.png "AutoML Engine pracuje v rozhraní příkazového řádku ML.NET")</span><span class="sxs-lookup"><span data-stu-id="a7ce2-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="a7ce2-117">Tyto prostředky můžete vygenerovat z vlastních datových sad, aniž byste je museli kódovat sami, takže také zlepší vaši produktivitu, i když už znáte ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="a7ce2-118">V současné době jsou úlohy ML podporované rozhraním příkazového řádku ML.NET:</span><span class="sxs-lookup"><span data-stu-id="a7ce2-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="a7ce2-119">klasifikace (binární a více tříd)</span><span class="sxs-lookup"><span data-stu-id="a7ce2-119">classification (binary and multi-class)</span></span>
- <span data-ttu-id="a7ce2-120">nevýhody</span><span class="sxs-lookup"><span data-stu-id="a7ce2-120">regression</span></span>
- <span data-ttu-id="a7ce2-121">základě</span><span class="sxs-lookup"><span data-stu-id="a7ce2-121">recommendation</span></span>
- <span data-ttu-id="a7ce2-122">Budoucí: další úlohy strojového učení, jako je například klasifikace imagí, hodnocení, detekce anomálií, clusteringu</span><span class="sxs-lookup"><span data-stu-id="a7ce2-122">Future: other machine learning tasks such as image-classification, ranking, anomaly-detection, clustering</span></span>

<span data-ttu-id="a7ce2-123">Příklad použití (klasifikační scénář):</span><span class="sxs-lookup"><span data-stu-id="a7ce2-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="a7ce2-125">Můžete ho spustit stejným způsobem jako v *prostředí Windows PowerShell*, *MacOS/Linux bash*nebo *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="a7ce2-126">Automatické dokončování v tabulkovém prostředí (návrhy parametrů) ale nebude fungovat ve *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="a7ce2-127">Vygenerované výstupní prostředky</span><span class="sxs-lookup"><span data-stu-id="a7ce2-127">Output assets generated</span></span>

<span data-ttu-id="a7ce2-128">Příkazy úkolu ML v rozhraní příkazového řádku generují následující prostředky ve výstupní složce:</span><span class="sxs-lookup"><span data-stu-id="a7ce2-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="a7ce2-129">Serializovaný model. zip ("nejlepší model") je připravený k použití ke spuštění předpovědi.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="a7ce2-130">Řešení C# s:</span><span class="sxs-lookup"><span data-stu-id="a7ce2-130">C# solution with:</span></span>
  - <span data-ttu-id="a7ce2-131">Kód jazyka C# ke spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="a7ce2-132">Kód jazyka C# s školicím kódem, který slouží ke generování tohoto modelu (pro účely učení nebo přeškolení modelu).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="a7ce2-133">Soubor protokolu s informacemi o všech iteracích/rozcyklcích v rámci více vyhodnocených algoritmů, včetně jejich podrobné konfigurace/kanálu.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="a7ce2-134">První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.) k tomu, aby se předpovědi s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="a7ce2-135">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete přesměrovat svůj model a prozkoumat a iterovat na to, které konkrétní Trainer/algoritmus a parametry byly vybrány rozhraním CLI a AutoML v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="a7ce2-136">Princip kvality modelu</span><span class="sxs-lookup"><span data-stu-id="a7ce2-136">Understanding the quality of the model</span></span>

<span data-ttu-id="a7ce2-137">Když vygenerujete "nejlepší model" pomocí nástroje CLI, uvidíte metriky kvality (například přesnost a R-kvadrát) podle potřeby pro úlohu ML, na kterou cílíte.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="a7ce2-138">Tady jsou tyto metriky shrnuté podle úkolu ML, abyste porozuměli kvalitě automaticky generovaného nejlepšího modelu.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="a7ce2-139">Metriky pro modely klasifikace</span><span class="sxs-lookup"><span data-stu-id="a7ce2-139">Metrics for Classification models</span></span>

<span data-ttu-id="a7ce2-140">V následujícím seznamu se zobrazí seznam metrik klasifikace pro nejoblíbenější pět modelů nalezené rozhraním příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="a7ce2-140">The following displays the classification metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="a7ce2-142">Přesnost je oblíbená metrika pro problémy s klasifikací, ale přesnost není vždy nejlepší metrikou pro výběr nejlepšího modelu, jak je vysvětleno v následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="a7ce2-143">Existují případy, kdy potřebujete vyhodnotit kvalitu modelu s dalšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="a7ce2-144">Pro zkoumání a pochopení metrik, které jsou výstupem rozhraní příkazového řádku, si přečtěte [metriky vyhodnocení pro klasifikaci](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="a7ce2-145">Metriky pro regrese a modely doporučení</span><span class="sxs-lookup"><span data-stu-id="a7ce2-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="a7ce2-146">Regresní model odpovídá datům, pokud jsou rozdíly mezi zjištěnými hodnotami a předpovězenými hodnotami modelu malé a neposunuté.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="a7ce2-147">Regresi je možné vyhodnotit pomocí určitých metrik.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="a7ce2-148">Zobrazí se podobný seznam metrik pro nejlépe pět modelů kvality, které rozhraní příkazového řádku najde.</span><span class="sxs-lookup"><span data-stu-id="a7ce2-148">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="a7ce2-149">V tomto konkrétním případě, který se týká úlohy regresní ML:</span><span class="sxs-lookup"><span data-stu-id="a7ce2-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="a7ce2-151">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku, přečtěte si téma [vyhodnocení metrik pro regresi](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="a7ce2-151">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="a7ce2-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7ce2-152">See also</span></span>

- [<span data-ttu-id="a7ce2-153">Postup instalace nástroje ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="a7ce2-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="a7ce2-154">Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="a7ce2-154">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="a7ce2-155">Reference k příkazům rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="a7ce2-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="a7ce2-156">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="a7ce2-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
