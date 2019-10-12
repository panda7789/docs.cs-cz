---
title: Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET
description: Zjistěte, jak pomocí nástroje CLI ML.NET automaticky proškolit nejlepší model z příkazového řádku.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: c147464ff59563d336363eed73fc6337bdb12e85
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275849"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="f2e1b-103">Automatizace školení modelů pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="f2e1b-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="f2e1b-104">ML.NET CLI "demokratizuje" ML.NET pro vývojáře v rozhraní .NET při učení ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="f2e1b-105">Pokud chcete používat rozhraní ML.NET API samostatně, (bez ML.NET AutoML CLI), musíte zvolit Trainer (implementaci algoritmu strojového učení pro konkrétní úlohu) a sadu transformací dat (metodologie funkcí), která se použije na vaše data.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="f2e1b-106">Optimální kanál se bude pro každou datovou sadu lišit a výběr optimálního algoritmu ze všech voleb zvyšuje složitost.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="f2e1b-107">Ještě více, každý algoritmus má sadu parametrů, které se mají vyladit.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="f2e1b-108">Proto můžete strávit týdny a někdy měsíce na optimalizaci modelů ve službě Machine Learning, které se snaží najít nejlepší kombinace funkcí pro inženýry, výukové algoritmy a základní parametry.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="f2e1b-109">Tento proces může být automatizovaný pomocí ML.NET CLI, který implementuje inteligentní modul ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="f2e1b-110">Toto téma odkazuje na ML.NET **CLI** a ml.NET **AutoML**, které jsou momentálně ve verzi Preview, a materiál může být změněn.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="f2e1b-111">Co je rozhraní příkazového řádku ML.NET (CLI)?</span><span class="sxs-lookup"><span data-stu-id="f2e1b-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="f2e1b-112">ML.NET CLI můžete spustit na jakémkoli příkazovém řádku (Windows, Mac nebo Linux) pro vytváření kvalitních ML.NET modelů a zdrojového kódu na základě vaší datové sady školení.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="f2e1b-113">Jak je znázorněno na následujícím obrázku, je jednoduché vytvořit vysoce kvalitní ML.NET model (soubor s serializovaným modelem. zip) a vzorový C# kód pro spuštění nebo určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="f2e1b-114">Kromě toho je vytvořen C# také kód pro vytvoření nebo výuku modelu, takže můžete prozkoumat a iterovat na algoritmus a nastavení použité pro vygenerovaný "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="f2e1b-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="f2e1b-115">![Image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine pracuje uvnitř ml.NET CLI") .</span><span class="sxs-lookup"><span data-stu-id="f2e1b-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="f2e1b-116">Tyto prostředky můžete vygenerovat z vlastních datových sad, aniž byste je museli kódovat sami, takže také zlepší vaši produktivitu, i když už znáte ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="f2e1b-117">V současné době jsou úlohy ML podporované rozhraním příkazového řádku ML.NET:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="f2e1b-118">Budoucnost: další úlohy strojového učení, například `recommendation`, `ranking` `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="f2e1b-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="f2e1b-119">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-119">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="f2e1b-121">Můžete ho spustit stejným způsobem jako v *prostředí Windows PowerShell*, \* MacOS/Linux bash nebo *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="f2e1b-122">Automatické dokončování v tabulkovém prostředí (návrhy parametrů) ale nebude fungovat ve *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="f2e1b-123">Vygenerované výstupní prostředky</span><span class="sxs-lookup"><span data-stu-id="f2e1b-123">Output assets generated</span></span>

<span data-ttu-id="f2e1b-124">Příkaz CLI `auto-train` generuje následující prostředky ve výstupní složce:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="f2e1b-125">Serializovaný model. zip ("nejlepší model") je připravený k použití ke spuštění předpovědi.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="f2e1b-126">C#řešení pomocí:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-126">C# solution with:</span></span>
  - <span data-ttu-id="f2e1b-127">C#kód pro spuštění nebo určení skóre generovaného modelu (k tomu, aby předpovědi v aplikacích pro koncové uživatele s tímto modelem).</span><span class="sxs-lookup"><span data-stu-id="f2e1b-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="f2e1b-128">C#kód s školicím kódem, který slouží ke generování tohoto modelu (pro účely učení nebo přeškolení modelu).</span><span class="sxs-lookup"><span data-stu-id="f2e1b-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="f2e1b-129">Soubor protokolu s informacemi o všech iteracích/rozcyklcích v rámci více vyhodnocených algoritmů, včetně jejich podrobné konfigurace/kanálu.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="f2e1b-130">První dva prostředky lze použít přímo v aplikacích pro koncové uživatele (ASP.NET Core webové aplikace, služby, aplikace klasické pracovní plochy atd.) k tomu, aby se předpovědi s tímto generovaným modelem ML.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="f2e1b-131">Třetí Asset a školicí kód vám ukáže, co ML.NET kód rozhraní API používal CLI k výuce vygenerovaného modelu, takže můžete přesměrovat svůj model a prozkoumat a iterovat, na kterém konkrétní Trainer/algoritmus a parametry byly vybrány rozhraním příkazového řádku a AutoML v části pokrývání.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="f2e1b-132">Princip kvality modelu</span><span class="sxs-lookup"><span data-stu-id="f2e1b-132">Understanding the quality of the model</span></span>

<span data-ttu-id="f2e1b-133">Když vygenerujete "nejlepší model" pomocí nástroje CLI, uvidíte metriky kvality (například přesnost a R-kvadrát) podle toho, jakou úlohu ML cílíte.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="f2e1b-134">Tady shrnujeme tyto metriky seskupené podle úkolu ML, abyste porozuměli kvalitě automaticky generovaného nejlepšího modelu.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="f2e1b-135">Metriky pro binární modely klasifikace</span><span class="sxs-lookup"><span data-stu-id="f2e1b-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="f2e1b-136">V následujícím seznamu se zobrazí seznam metriky úlohy binární klasifikace v ML pro nejoblíbenější pět modelů nalezené rozhraním příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="f2e1b-138">Přesnost je oblíbená metrika pro problémy s klasifikací, ale přesnost není vždy nejlepší metrikou pro výběr nejlepšího modelu, jak je vysvětleno v níže uvedených odkazech.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="f2e1b-139">Existují případy, kdy potřebujete vyhodnotit kvalitu modelu s dalšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="f2e1b-140">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku, přečtěte si téma [metriky pro binární klasifikaci](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="f2e1b-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="f2e1b-141">Metriky pro modely klasifikace s více třídami</span><span class="sxs-lookup"><span data-stu-id="f2e1b-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="f2e1b-142">Následující seznam zobrazuje seznam metrik úlohy klasifikace s více třídami pro nejoblíbenější pět modelů nalezené rozhraním příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="f2e1b-144">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku, přečtěte si téma [metriky pro klasifikaci s více třídami](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="f2e1b-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="f2e1b-145">Metriky pro regresní modely</span><span class="sxs-lookup"><span data-stu-id="f2e1b-145">Metrics for Regression models</span></span>

<span data-ttu-id="f2e1b-146">Regresní model odpovídá datům, pokud jsou rozdíly mezi zjištěnými hodnotami a předpovězenými hodnotami modelu malé a neposunuté.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="f2e1b-147">Regresi je možné vyhodnotit pomocí určitých metrik.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="f2e1b-148">Zobrazí se podobný seznam metrik pro nejlépe pět modelů kvality, které rozhraní příkazového řádku najde.</span><span class="sxs-lookup"><span data-stu-id="f2e1b-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="f2e1b-149">V tomto konkrétním případě, který se týká úlohy regresní ML:</span><span class="sxs-lookup"><span data-stu-id="f2e1b-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="f2e1b-151">Chcete-li prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku, přečtěte si téma [metriky pro regresi](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="f2e1b-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2e1b-152">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="f2e1b-152">See also</span></span>

- [<span data-ttu-id="f2e1b-153">Postup instalace nástroje ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="f2e1b-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="f2e1b-154">Kurz: automatické generování binárního klasifikátoru pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="f2e1b-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="f2e1b-155">Reference k příkazům rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="f2e1b-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="f2e1b-156">Telemetrie v ML.NET CLI</span><span class="sxs-lookup"><span data-stu-id="f2e1b-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
