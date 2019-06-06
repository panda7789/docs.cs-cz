---
title: Příkaz automaticky trénování v nástroji příkazového řádku ML.NET
description: Přehled ukázky a referenční informace pro příkaz automaticky trénování v nástroji ML.NET rozhraní příkazového řádku.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: ce5994f392c492e80676b9e65ce54fe010cf03ab
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722610"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="6afad-103">Příkaz "automaticky – train" v rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="6afad-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="6afad-104">Toto téma odkazuje na ML.NET rozhraní příkazového řádku a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="6afad-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="6afad-105">`auto-train` Příkaz je hlavní příkaz poskytnutých nástrojem ML.NET rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="6afad-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="6afad-106">Tento příkaz umožňuje vygenerovat modelu ML.NET kvalitních (serializovaný model soubor .zip) plus v příkladu C# kód pro spuštění/určení skóre modelu.</span><span class="sxs-lookup"><span data-stu-id="6afad-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="6afad-107">Kromě toho C# kód k vytvoření a trénování modelu také vygeneruje se pro vás Chcete-li zjistit, jaké algoritmus a nastavení používá pro, který vygeneruje "nejlepší model".</span><span class="sxs-lookup"><span data-stu-id="6afad-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="6afad-108">Tyto prostředky můžete vygenerovat z vlastní datové sady bez kódování sami, tak i v případě, že již znáte ML.NET také zlepšuje produktivitu.</span><span class="sxs-lookup"><span data-stu-id="6afad-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="6afad-109">V současné době nepodporuje rozhraní příkazového řádku ML.NET úlohy ML jsou:</span><span class="sxs-lookup"><span data-stu-id="6afad-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="6afad-110">Budoucnost: Další strojového učení úlohy, jako například</span><span class="sxs-lookup"><span data-stu-id="6afad-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="6afad-111">Příklad použití na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="6afad-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="6afad-112">`mlnet auto-train` Příkaz vytvoří následující prostředky:</span><span class="sxs-lookup"><span data-stu-id="6afad-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="6afad-113">Serializovaný model soubor .zip ("nejlepší model") připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="6afad-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="6afad-114">C#vytvořit kód pro spuštění/skóre, které model (k následné predikci ve vašich aplikacích koncového uživatele pomocí tohoto modelu).</span><span class="sxs-lookup"><span data-stu-id="6afad-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="6afad-115">C#kód s kódem školení sloužící ke generování tohoto modelu (výukové účely).</span><span class="sxs-lookup"><span data-stu-id="6afad-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="6afad-116">První dva prostředky lze použít přímo v aplikacích s koncovým uživatelem (webové aplikace ASP.NET Core, služby, aplikace klasické pracovní plochy, atd.) k následné predikci s generovanou modelu ML.</span><span class="sxs-lookup"><span data-stu-id="6afad-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="6afad-117">Třetí asset školení kód ukazuje, jaký kód ML.NET API rozhraní příkazového řádku použil tak moct trénovat vygenerovaný model, takže si můžete zjistit, jaké konkrétní trainer/algoritmus a hyper-paramenters byly vybrány tak, že rozhraní příkazového řádku a modul ML.NET AutoML.</span><span class="sxs-lookup"><span data-stu-id="6afad-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-paramenters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="6afad-118">Příkaz "automaticky – train" používá modul AutoML</span><span class="sxs-lookup"><span data-stu-id="6afad-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="6afad-119">Rozhraní příkazového řádku používá modul ML.NET AutoML (balíček NuGet) k vyhledání inteligentně nejlepší kvality modelů, jak je znázorněno v následujícím diagramu:</span><span class="sxs-lookup"><span data-stu-id="6afad-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="6afad-120">![Obrázek](./media/ml-net-automl-working-diagram.png "AutoML modul práci uvnitř rozhraní příkazového řádku ML.NET")</span><span class="sxs-lookup"><span data-stu-id="6afad-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="6afad-121">Při spuštění nástroje příkazového řádku ML.NET s "Automatické – train příkaz, zobrazí se vám nástroj při více iterací s využitím různých algoritmů a kombinace konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6afad-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="6afad-122">Referenční informace pro příkaz "Automatické – train"</span><span class="sxs-lookup"><span data-stu-id="6afad-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="6afad-123">Příklady</span><span class="sxs-lookup"><span data-stu-id="6afad-123">Examples</span></span>

<span data-ttu-id="6afad-124">Nejjednodušší příkazu rozhraní příkazového řádku pro binárního klasifikačního problému (AutoML bude nutné odvodit většinu položek konfigurace z poskytnutá data):</span><span class="sxs-lookup"><span data-stu-id="6afad-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="6afad-125">Jiné jednoduchého příkazu rozhraní příkazového řádku pro regresní problém:</span><span class="sxs-lookup"><span data-stu-id="6afad-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="6afad-126">Vytvoření a trénování modelu binární klasifikace s trénování datové sady, testovací datové sady a další přizpůsobení explicitní argumenty:</span><span class="sxs-lookup"><span data-stu-id="6afad-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="6afad-127">Name</span><span class="sxs-lookup"><span data-stu-id="6afad-127">Name</span></span>

<span data-ttu-id="6afad-128">`mlnet auto-train` -Trénovat různé modely (n iterací) podle zadané datové sady a nakonec vybere nejlepší model, uloží ho jako soubor ZIP serializovaná plus generuje související C# kód pro vyhodnocování a školení.</span><span class="sxs-lookup"><span data-stu-id="6afad-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6afad-129">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6afad-129">Synopsis</span></span>

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="6afad-130">Neplatné vstupní možnosti by neměly způsobit nástroj rozhraní příkazového řádku a vygenerovat seznam platné vstupy a chybová zpráva s vysvětlením které arg chybí, pokud je to tento případ.</span><span class="sxs-lookup"><span data-stu-id="6afad-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="6afad-131">Možnosti</span><span class="sxs-lookup"><span data-stu-id="6afad-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="6afad-132">`--task | --mltask | -T` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="6afad-133">Jeden řetězec, který poskytuje ML problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="6afad-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="6afad-134">Například některé z těchto úloh (příkazového řádku nakonec bude podporovat všechny úkoly, které jsou podporovány v AutoML):</span><span class="sxs-lookup"><span data-stu-id="6afad-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="6afad-135">`regression` – Vyberte, pokud modelu ML se použije k předvídání číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="6afad-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="6afad-136">`binary-classification` – Vyberte, pokud výsledek modelu ML má dva možné zařazené do kategorií logické hodnoty (0 nebo 1).</span><span class="sxs-lookup"><span data-stu-id="6afad-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="6afad-137">`multiclass-classification` – Vyberte, pokud modelu ML výsledek obsahuje více kategorií možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="6afad-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="6afad-138">V budoucnu uvolňuje další ML úlohy a scénáře, jako `recommendations`, `clustering` a `ranking` bude podporovat.</span><span class="sxs-lookup"><span data-stu-id="6afad-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="6afad-139">V tomto argumentu musí být zadána pouze jedna ML úloh.</span><span class="sxs-lookup"><span data-stu-id="6afad-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="6afad-140">`--dataset | -d` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="6afad-141">Tento argument obsahuje cestu k jedné z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="6afad-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="6afad-142">*A: Soubor celé datové sady:* Pokud tuto možnost a uživatel neposkytuje `--test-dataset` a `--validation-dataset`, pak křížového ověření (k přeložení atd.) nebo automatizovaných datových rozdělit přístupy se interně používá k ověření modelu.</span><span class="sxs-lookup"><span data-stu-id="6afad-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="6afad-143">Uživatel v takovém případě stačí muset zadat cestu datové sady.</span><span class="sxs-lookup"><span data-stu-id="6afad-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="6afad-144">*B: Soubor trénovací datové sady:* Pokud uživatel také nabízí datové sady pro ověření modelu (pomocí `--test-dataset` a volitelně `--validation-dataset`), pak bude `--dataset` argument znamená, že stačí, když "trénovací datové sady".</span><span class="sxs-lookup"><span data-stu-id="6afad-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="6afad-145">Například při použití 80 % 20 % přístup k ověření kvality modelu a získat metriky přesnosti, bude mít "trénovací datové sady" 80 % dat a "test dataset" bude mít 20 % data.</span><span class="sxs-lookup"><span data-stu-id="6afad-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-146">`--test-dataset | -t` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="6afad-147">Cesta k souboru odkazující na soubor datové sady testů, například při použití 80 % 20 % přístup při provádění pravidelných ověření získat metriky přesnosti.</span><span class="sxs-lookup"><span data-stu-id="6afad-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="6afad-148">Pokud používáte `--test-dataset`, pak `--dataset` je také nutný.</span><span class="sxs-lookup"><span data-stu-id="6afad-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="6afad-149">`--test-dataset` Argument je nepovinný Pokud--ověření datová sada použije.</span><span class="sxs-lookup"><span data-stu-id="6afad-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="6afad-150">V takovém případě musí uživatel použít tři argumenty.</span><span class="sxs-lookup"><span data-stu-id="6afad-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-151">`--validation-dataset | -v` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="6afad-152">Cesta k souboru odkazující na soubor datové sady ověřování.</span><span class="sxs-lookup"><span data-stu-id="6afad-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="6afad-153">Ověření datové sady je volitelný, v každém případě.</span><span class="sxs-lookup"><span data-stu-id="6afad-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="6afad-154">Pokud se používá `validation dataset`, by měla být chování:</span><span class="sxs-lookup"><span data-stu-id="6afad-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="6afad-155">`test-dataset` a `--dataset` argumenty jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="6afad-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="6afad-156">`validation-dataset` Datová sada použije k odhadu chyba předpovědi modelu výběru.</span><span class="sxs-lookup"><span data-stu-id="6afad-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="6afad-157">`test-dataset` Se používá pro účely posouzení chyby generalizace konečného zvolili modelu.</span><span class="sxs-lookup"><span data-stu-id="6afad-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="6afad-158">V ideálním případě testovací sada nutné udržovat v "úložiště" a být přenesena pouze na konci analýza dat.</span><span class="sxs-lookup"><span data-stu-id="6afad-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="6afad-159">V podstatě při použití `validation dataset` plus `test dataset`, fázi ověřování je rozdělený do dvou částí:</span><span class="sxs-lookup"><span data-stu-id="6afad-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="6afad-160">V první části vám stačí podívejte se na vaše modely a vybrat nejvýkonnější přístupem pomocí ověření dat (tzn. ověření)</span><span class="sxs-lookup"><span data-stu-id="6afad-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="6afad-161">Potom odhadnout přesnost vybrané přístup (= test).</span><span class="sxs-lookup"><span data-stu-id="6afad-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="6afad-162">Oddělení dat může být proto, 80/10/10 nebo 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="6afad-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="6afad-163">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6afad-163">For example:</span></span>

- <span data-ttu-id="6afad-164">`training-dataset` soubor by měl mít 75 % data.</span><span class="sxs-lookup"><span data-stu-id="6afad-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="6afad-165">`validation-dataset` soubor by měl mít 15 % této data.</span><span class="sxs-lookup"><span data-stu-id="6afad-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="6afad-166">`test-dataset` soubor by měl mít 10 % data.</span><span class="sxs-lookup"><span data-stu-id="6afad-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="6afad-167">V každém případě tyto procenta bude rozhodnuto pomocí uživatele pomocí rozhraní příkazového řádku, který poskytne že soubory již rozdělit.</span><span class="sxs-lookup"><span data-stu-id="6afad-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-168">`--label-column-name | -n` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="6afad-169">Díky tomuto argumentu konkrétní cíle a cílový sloupec (proměnné, kterou chcete předpovědět) lze zadat pomocí názvu sloupce nastavit v hlavičce datové sady.</span><span class="sxs-lookup"><span data-stu-id="6afad-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="6afad-170">Tento argument se používá pouze pro úkoly, jsou pod dohledem ML, jako *klasifikace problému*.</span><span class="sxs-lookup"><span data-stu-id="6afad-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="6afad-171">Jej nelze použít bez dohledu ML úkoly, jako *clustering*.</span><span class="sxs-lookup"><span data-stu-id="6afad-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-172">`--label-column-index | -i` (int).</span><span class="sxs-lookup"><span data-stu-id="6afad-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="6afad-173">Díky tomuto argumentu se dá nastavit konkrétní cíle a cílový sloupec (proměnné, kterou chcete předpovědět) s použitím sloupce číselného indexu v souboru datové sady (sloupec hodnoty indexů začínají 1).</span><span class="sxs-lookup"><span data-stu-id="6afad-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="6afad-174">*Poznámka:* Pokud uživatel používá také `--label-column-name`, `--label-column-name` je používán.</span><span class="sxs-lookup"><span data-stu-id="6afad-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="6afad-175">Tento argument se používá pouze pro pod dohledem ML úloh, jako *klasifikace problému*.</span><span class="sxs-lookup"><span data-stu-id="6afad-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="6afad-176">Jej nelze použít bez dohledu ML úkoly, jako *clustering*.</span><span class="sxs-lookup"><span data-stu-id="6afad-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-177">`--ignore-columns | -I` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="6afad-178">Díky tomuto argumentu můžete ignorovat existujících sloupců v souboru datové sady, nejsou načteny a využívané procesy trénování.</span><span class="sxs-lookup"><span data-stu-id="6afad-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="6afad-179">Zadejte názvy sloupců, které má být ignorována.</span><span class="sxs-lookup"><span data-stu-id="6afad-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="6afad-180">Použití "," (čárkou mezera) nebo ". (místo) k oddělení více názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="6afad-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="6afad-181">Pro názvy sloupců obsahující prázdné znaky (například "přihlášení") můžete použít uvozovky.</span><span class="sxs-lookup"><span data-stu-id="6afad-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="6afad-182">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6afad-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="6afad-183">`--has-header | -h` (bool)</span><span class="sxs-lookup"><span data-stu-id="6afad-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="6afad-184">Zadejte, pokud soubory datové sady mají řádek záhlaví.</span><span class="sxs-lookup"><span data-stu-id="6afad-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="6afad-185">Možné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="6afad-185">Possible values are:</span></span>
- `true`
- `false`

<span data-ttu-id="6afad-186">Ve výchozím nastavení je hodnota `true` Pokud tento argument nezadá uživatel.</span><span class="sxs-lookup"><span data-stu-id="6afad-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="6afad-187">Chcete-li použít `--label-column-name` argument, musíte mít záhlaví v souboru datové sady a `--has-header` nastavena na `true` (což je ve výchozím nastavení).</span><span class="sxs-lookup"><span data-stu-id="6afad-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-188">`--max-exploration-time | -x` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="6afad-189">Ve výchozím nastavení průzkum maximální doba je 30 minut.</span><span class="sxs-lookup"><span data-stu-id="6afad-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="6afad-190">Tento argument Nastaví maximální dobu (v sekundách) pro proces k prozkoumání více školitelé a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6afad-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="6afad-191">Pokud zadaná doba je příliš krátká (třeba 2 sekundy) pro jednu iteraci, může být překročena nastavená doba.</span><span class="sxs-lookup"><span data-stu-id="6afad-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="6afad-192">V tomto případě skutečný čas je čas potřebný k vytvoření jedné konfigurace modelu v jedné iterace.</span><span class="sxs-lookup"><span data-stu-id="6afad-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="6afad-193">Potřebná doba pro iterace se může lišit v závislosti na velikosti datové sady.</span><span class="sxs-lookup"><span data-stu-id="6afad-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-194">`--cache | -c` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="6afad-195">Používáte-li ukládání do mezipaměti, bude celý trénovací datové sady načten v paměti.</span><span class="sxs-lookup"><span data-stu-id="6afad-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="6afad-196">Pro malé a středně velké datové sady může použití mezipaměti výrazně zlepšit výkon školení, což znamená, že čas školení může být kratší než není při použití mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6afad-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="6afad-197">Ale velkých datových sad, načítání všech dat v paměti může negativně vzhledem k tomu, že se mohou zobrazovat nedostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="6afad-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="6afad-198">Při školení s velkou datovou sadu souborů a bez použití mezipaměti ML.NET bude možné streamování bloky dat z jednotky když je nutné načíst větší množství dat. při školení.</span><span class="sxs-lookup"><span data-stu-id="6afad-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="6afad-199">Můžete zadat následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="6afad-199">You can specify the following values:</span></span>

<span data-ttu-id="6afad-200">`on`: Vynutí mezipaměti má být použit při školení.</span><span class="sxs-lookup"><span data-stu-id="6afad-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="6afad-201">`off`: Vynutí mezipaměti není pro použití při cvičení.</span><span class="sxs-lookup"><span data-stu-id="6afad-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="6afad-202">`auto`: V závislosti na AutoML heuristickými metodami mezipaměti se použije, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6afad-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="6afad-203">Obvykle malé a střední datové sady využije mezipaměti a velkých datových sad nepoužije mezipaměti, pokud použijete `auto` podle výběru.</span><span class="sxs-lookup"><span data-stu-id="6afad-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="6afad-204">Pokud nezadáte `--cache` parametr a potom mezipaměti `auto` konfigurace se použije ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6afad-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-205">`--name | -N` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-205">`--name | -N` (string)</span></span>

<span data-ttu-id="6afad-206">Název pro výstup vytvořený projekt nebo řešení.</span><span class="sxs-lookup"><span data-stu-id="6afad-206">The name for the created output project or solution.</span></span> <span data-ttu-id="6afad-207">Pokud není zadán žádný název, název `sample-{mltask}` se používá.</span><span class="sxs-lookup"><span data-stu-id="6afad-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="6afad-208">Soubor modelu ML.NET (. Soubor ZIP) získáte stejný název, také.</span><span class="sxs-lookup"><span data-stu-id="6afad-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-209">`--output-path | -o` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="6afad-210">Kořenové umístění/složky umístit vygenerovaný výstup.</span><span class="sxs-lookup"><span data-stu-id="6afad-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="6afad-211">Výchozí je aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6afad-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="6afad-212">`--verbosity | -V` (string)</span><span class="sxs-lookup"><span data-stu-id="6afad-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="6afad-213">Nastaví úroveň podrobností ve standardním výstupu.</span><span class="sxs-lookup"><span data-stu-id="6afad-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="6afad-214">Povolené hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6afad-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="6afad-215">`m[inimal]`  (ve výchozím nastavení)</span><span class="sxs-lookup"><span data-stu-id="6afad-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="6afad-216">`diag[nostic]` (informace o úroveň protokolování)</span><span class="sxs-lookup"><span data-stu-id="6afad-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="6afad-217">Ve výchozím nastavení nástroj rozhraní příkazového řádku by se zobrazit některé minimální zpětnou vazbu (minimální) při práci, jako je uvedení, že funguje a pokud je to možné kolik času je left nebo co společnost % času dokončení.</span><span class="sxs-lookup"><span data-stu-id="6afad-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="6afad-218">Vytiskne nápovědy pro příkaz s popisem pro každý příkaz parametr.</span><span class="sxs-lookup"><span data-stu-id="6afad-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="6afad-219">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6afad-219">See also</span></span>

- [<span data-ttu-id="6afad-220">Postup instalace nástroje rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="6afad-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="6afad-221">Automatizace trénování modelu s využitím rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="6afad-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="6afad-222">Kurz: Automaticky generovat binární klasifikátor pomocí rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="6afad-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="6afad-223">Telemetrie v rozhraní příkazového řádku ML.NET</span><span class="sxs-lookup"><span data-stu-id="6afad-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
