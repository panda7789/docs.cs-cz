---
title: Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET
description: Objevte, jak pomocí nástroje příkazového řádku ML.NET automaticky trénování nejlepší model z příkazového řádku.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: 33383582140d9df4290a0bbf30659301af837d1d
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066262"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="5a4b4-103">Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="5a4b4-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="5a4b4-104">Rozhraní příkazového řádku ML.NET "demokratizuje" ML.NET pro vývojáře na platformě .NET při učení ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="5a4b4-105">K používání rozhraní API ML.NET samostatně, (bez rozhraní příkazového řádku AutoML ML.NET) musíte zvolit trainer (provádění algoritmu strojového učení pro určité úlohy) a sadu transformace dat (vytváření funkcí) použít k vašim datům.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="5a4b4-106">Optimální kanál se budou lišit pro každou datovou sadu a výběr optimálního algoritmu ze všech možností přidá na složitost.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="5a4b4-107">Ještě více jednotlivých algoritmus využívající dlaždice má sadu hyperparameters ladit.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="5a4b4-108">Proto můžete věnovat týdnů a někdy měsíců na strojového učení při hledání nejlepších kombinace vytváření funkcí, algoritmů učení a hyperparameters optimalizace modelu.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="5a4b4-109">Tento proces je možné automatizovat pomocí rozhraní příkazového řádku ML.NET, která implementuje modul inteligentních ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span> 

> [!NOTE]
> <span data-ttu-id="5a4b4-110">Toto téma odkazuje na ML.NET **rozhraní příkazového řádku** a ML.NET **AutoML**, které jsou aktuálně ve verzi Preview a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span> 

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="5a4b4-111">Co je ML.NET rozhraní příkazového řádku (CLI)?</span><span class="sxs-lookup"><span data-stu-id="5a4b4-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="5a4b4-112">Rozhraní příkazového řádku ML.NET můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) pro vytváření kvalitní ML.NET modely a zdrojový kód založený na trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="5a4b4-113">Jak je znázorněno na následujícím obrázku, je to jednoduché ke generování modelu ML.NET vysoce kvalitní (serializovaný model soubor .zip) plus vzorku C# kód pro spuštění/určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="5a4b4-114">Kromě toho C# k vytvoření a trénování modelu také generování kódu, takže můžete prozkoumat a iterovat algoritmu a nastavení, která vygeneruje "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="5a4b4-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span> 

<span data-ttu-id="5a4b4-115">![Obrázek](media/automate-training-with-cli/cli-high-level-process.png "AutoML modul práci uvnitř rozhraní příkazového řádku ML.NET")</span><span class="sxs-lookup"><span data-stu-id="5a4b4-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="5a4b4-116">Tyto prostředky můžete vygenerovat z vlastní datové sady bez kódování sami, tak i v případě, že již znáte ML.NET také zlepšuje produktivitu.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="5a4b4-117">V současné době nepodporuje rozhraní příkazového řádku ML.NET úlohy ML jsou:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification` 
- `regression`
- <span data-ttu-id="5a4b4-118">Budoucnost: jiných strojového učení s úkoly, jako `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="5a4b4-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="5a4b4-119">Příklad použití:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-119">Example of usage:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![obrázek](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="5a4b4-121">Můžete ji spustit stejný způsobem on *prostředí Windows PowerShell*, \* bash v systému macOS nebo Linux, nebo *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="5a4b4-122">Ale tabulkové automatického dokončování (parametr návrhy) nebudou fungovat ve *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="5a4b4-123">Vygeneruje výstupní assety</span><span class="sxs-lookup"><span data-stu-id="5a4b4-123">Output assets generated</span></span>

<span data-ttu-id="5a4b4-124">Rozhraní příkazového řádku `auto-train` příkaz vytvoří následující prostředky ve výstupní složce:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="5a4b4-125">Serializovaný model soubor .zip ("nejlepší model") připravený k použití pro spouštěním predikcí.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span> 
- <span data-ttu-id="5a4b4-126">C#řešení:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-126">C# solution with:</span></span>
    - <span data-ttu-id="5a4b4-127">C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).</span><span class="sxs-lookup"><span data-stu-id="5a4b4-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="5a4b4-128">C#kód s kódem školení sloužící ke generování tohoto modelu (pro výukové účely nebo přetrénování modelů).</span><span class="sxs-lookup"><span data-stu-id="5a4b4-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="5a4b4-129">Soubor protokolu s informacemi o všech iterací/změny napříč několika algoritmů vyhodnotí, včetně jejich podrobné konfigurace/kanálu.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="5a4b4-130">První dva prostředky lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovanou modelu ML.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="5a4b4-131">Třetí asset školení kód ukazuje, můžete kód ML.NET API použil rozhraní příkazového řádku pro trénování modelu vygenerovaný, tak přeučování váš model, prozkoumat a iterovat na jaké konkrétní trainer/algoritmu a hyperparameters byly vybrány tak, že rozhraní příkazového řádku a AutoML pod pokličkou.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span> 

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="5a4b4-132">Principy kvality tohoto modelu</span><span class="sxs-lookup"><span data-stu-id="5a4b4-132">Understanding the quality of the model</span></span>

<span data-ttu-id="5a4b4-133">Při generování "nejlepší model" pomocí nástroje příkazového řádku zobrazí metrik kvality (jako jsou správnost a spolehlivosti R) v závislosti na ML úkol, který cílíte.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="5a4b4-134">Tady Shrneme informace z těchto metrik seskupené podle úlohy ML to vám umožní pochopit kvality vaší auto-generated "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="5a4b4-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="5a4b4-135">Metriky pro binární klasifikační modely</span><span class="sxs-lookup"><span data-stu-id="5a4b4-135">Metrics for Binary Classification models</span></span>

 <span data-ttu-id="5a4b4-136">Následující seznam binární klasifikace ML úloh metrik pro hlavní pět modelů nalezené pomocí rozhraní příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span> 

![obrázek](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="5a4b4-138">Přesnost je Oblíbené metriky pro klasifikaci problémy, ale přesnost není vždy nejlepší metrika vybrat nejlepší model z jak je vysvětleno v odkazech níže.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="5a4b4-139">Existují případy, kdy potřebujete pro vyhodnocení kvality modelu pomocí další metriky.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="5a4b4-140">Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro binární klasifikaci](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="5a4b4-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="5a4b4-141">Metriky pro modelů klasifikace víc tříd</span><span class="sxs-lookup"><span data-stu-id="5a4b4-141">Metrics for Multi-class Classification models</span></span>

 <span data-ttu-id="5a4b4-142">Následující zobrazí seznam klasifikací roc ML úloh metrik pro hlavní pět modelů nalezené pomocí rozhraní příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span> 

![obrázek](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="5a4b4-144">Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro klasifikace víc tříd](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="5a4b4-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="5a4b4-145">Metriky pro regresní modely</span><span class="sxs-lookup"><span data-stu-id="5a4b4-145">Metrics for Regression models</span></span>

<span data-ttu-id="5a4b4-146">Regresní model odpovídá zpracovávaným datům, pokud jsou rozdíly mezi zjištěnou hodnoty a modelu předpovězeným hodnotám malé a neposunutého.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="5a4b4-147">Regrese mohou být vyhodnoceny s určité metriky.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="5a4b4-148">Zobrazí se podobná seznam metrik pro nejlepší nejvyšší kvality pět modelů nalezené pomocí rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5a4b4-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="5a4b4-149">V tomto konkrétním případě související regrese ML úlohy:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-149">In this particular case related to a regression ML task:</span></span>

![obrázek](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="5a4b4-151">Prozkoumat a pochopit metriky, které jsou výstupem rozhraní příkazového řádku najdete v tématu [metriky pro regresní](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="5a4b4-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a4b4-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a4b4-152">See also</span></span>

- [<span data-ttu-id="5a4b4-153">Postup instalace nástroje rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="5a4b4-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="5a4b4-154">Kurz: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="5a4b4-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="5a4b4-155">Reference k příkazům rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="5a4b4-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="5a4b4-156">Telemetrie v rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="5a4b4-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
