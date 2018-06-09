---
title: Machine Learning Glosář
description: Glosář termínů machine learning.
author: jralexander
ms.author: johalex
ms.date: 05/31/2018
ms.topic: conceptual
ms.prod: dotnet-ml
ms.devlang: dotnet
manager: wpickett
ms.openlocfilehash: 332d9e14bea165992f9f00b048286e185269ea79
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2018
ms.locfileid: "35017272"
---
# <a name="machine-learning-glossary"></a><span data-ttu-id="bfe2c-103">Machine learning Glosář</span><span class="sxs-lookup"><span data-stu-id="bfe2c-103">Machine learning glossary</span></span>

<span data-ttu-id="bfe2c-104">V následujícím seznamu je kompilací důležité machine learning podmínky, které jsou užitečné při sestavování vlastní modely.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-104">The following list is a compilation of important machine learning terms that are useful as you build your custom models.</span></span>

## <a name="accuracy"></a><span data-ttu-id="bfe2c-105">Přesnost</span><span class="sxs-lookup"><span data-stu-id="bfe2c-105">Accuracy</span></span>

<span data-ttu-id="bfe2c-106">V [klasifikace](#classification), přesnost je počet správně klasifikovaný položek oddělených celkový počet položek v sadě testů.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-106">In [classification](#classification), accuracy is the number of correctly classified items divided by the total number of items in the test set.</span></span> <span data-ttu-id="bfe2c-107">Rozmezí od 0 (nejméně přesné) na hodnotu 1 (nejpřesnější).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-107">Ranges from 0 (least accurate) to 1 (most accurate).</span></span> <span data-ttu-id="bfe2c-108">Přesnost je jedním z vyhodnocení metriky výkonu modelu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-108">Accuracy is one of evaluation metrics of the performance of your model.</span></span> <span data-ttu-id="bfe2c-109">Zvažte ve spojení s [přesnost](#precision), [odvolání](#recall), a [F – score](#f-score).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-109">Consider it in conjunction with [precision](#precision), [recall](#recall), and [F-score](#f-score).</span></span>

<span data-ttu-id="bfe2c-110">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-110">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Accuracy?displayProperty=nameWithType>.</span></span>

## <a name="area-under-the-curve-auc"></a><span data-ttu-id="bfe2c-111">Oblast pod křivkou (AUC)</span><span class="sxs-lookup"><span data-stu-id="bfe2c-111">Area under the curve (AUC)</span></span>

<span data-ttu-id="bfe2c-112">V [binární klasifikace](#binary-classification), metriku hodnocení, která je hodnota oblasti pod křivkou, která ukazuje zeměpisný true pozitivních rychlost (na ose y) proti falešně pozitivních rychlost (na ose x).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-112">In [binary classification](#binary-classification), an evaluation metric that is the value of the area under the curve that plots the true positives rate (on the y-axis) against the false positives rate (on the x-axis).</span></span> <span data-ttu-id="bfe2c-113">Rozsahy z 0,5 (nejhorší) na hodnotu 1 (doporučené).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-113">Ranges from 0.5 (worst) to 1 (best).</span></span> <span data-ttu-id="bfe2c-114">Oblasti se taky říká pod křivka ROC, tedy příjemce operační charakteristik křivky.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-114">Also known as the area under the ROC curve, i.e., receiver operating characteristic curve.</span></span> <span data-ttu-id="bfe2c-115">Další informace najdete v tématu [příjemce operační vlastnosti](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-115">For more information, see the [Receiver operating characteristic](https://en.wikipedia.org/wiki/Receiver_operating_characteristic) article on Wikipedia.</span></span>

<span data-ttu-id="bfe2c-116">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-116">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.Auc?displayProperty=nameWithType>.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="bfe2c-117">binární klasifikace</span><span class="sxs-lookup"><span data-stu-id="bfe2c-117">Binary classification</span></span>

<span data-ttu-id="bfe2c-118">A [klasifikace](#classification) případ where [popisek](#label) je jenom jednu z dvě třídy.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-118">A [classification](#classification) case where the [label](#label) is only one out of two classes.</span></span> <span data-ttu-id="bfe2c-119">Další informace najdete v tématu [binární klasifikace](https://en.wikipedia.org/wiki/Binary_classification) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

## <a name="classification"></a><span data-ttu-id="bfe2c-120">klasifikace</span><span class="sxs-lookup"><span data-stu-id="bfe2c-120">Classification</span></span>

<span data-ttu-id="bfe2c-121">Pokud data se používají k předvídání kategorii, [počítač učení se supervizí](#supervised-machine-learning) je volána úloha, klasifikace.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-121">When the data is used to predict a category, [supervised machine learning](#supervised-machine-learning) task is called classification.</span></span> <span data-ttu-id="bfe2c-122">[Binární klasifikace](#binary-classification) odkazuje na predikci pouze dvě kategorie (například klasifikace bitovou kopii jako obrázek 'cat' nebo 'PSA).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-122">[Binary classification](#binary-classification) refers to predicting only two categories (for example, classifying an image as a picture of either a 'cat' or a 'dog').</span></span> <span data-ttu-id="bfe2c-123">[Více třídami klasifikace](#multiclass-classification) odkazuje na predikci více kategorií (například při klasifikaci bitovou kopii jako obrázek konkrétní druh PSA).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-123">[Multiclass classification](#multiclass-classification) refers to predicting multiple categories (for example, when classifying an image as a picture of a specific breed of dog).</span></span>

## <a name="coefficient-of-determination"></a><span data-ttu-id="bfe2c-124">Koeficient spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="bfe2c-124">Coefficient of determination</span></span>

<span data-ttu-id="bfe2c-125">V [regrese](#regression), metriku hodnocení, která určuje, jak dobře dat odpovídá modelu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-125">In [regression](#regression), an evaluation metric that indicates how well data fits a model.</span></span> <span data-ttu-id="bfe2c-126">Rozmezí od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-126">Ranges from 0 to 1.</span></span> <span data-ttu-id="bfe2c-127">Hodnota 0 znamená, že data jsou náhodných nebo jinak se nemůže vejít do modelu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-127">A value of 0 means that the data is random or otherwise cannot be fit to the model.</span></span> <span data-ttu-id="bfe2c-128">Hodnota 1 znamená, že model přesně odpovídá data.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-128">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="bfe2c-129">To se často označuje jako r<sup>2</sup>, R<sup>2</sup>, nebo spolehlivosti.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-129">This is often referred to as r<sup>2</sup>, R<sup>2</sup>, or r-squared.</span></span>

<span data-ttu-id="bfe2c-130">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-130">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.RSquared?displayProperty=nameWithType>.</span></span>

## <a name="feature"></a><span data-ttu-id="bfe2c-131">Funkce</span><span class="sxs-lookup"><span data-stu-id="bfe2c-131">Feature</span></span>

<span data-ttu-id="bfe2c-132">Měřitelné vlastnosti jevu měřenou, obvykle číselnou hodnotu (double).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-132">A measurable property of the phenomenon being measured, typically a numeric (double) value.</span></span> <span data-ttu-id="bfe2c-133">Více funkcí se označují jako **funkce vector** a obvykle se uloží jako `double[]`.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-133">Multiple features are referred to as a **Feature vector** and typically stored as `double[]`.</span></span> <span data-ttu-id="bfe2c-134">Funkce definovat důležité charakteristiky se měří jevu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-134">Features define the important characteristics of the phenomenon being measured.</span></span> <span data-ttu-id="bfe2c-135">Další informace najdete v tématu [funkce](https://en.wikipedia.org/wiki/Feature_(machine_learning)) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-135">For more information, see the [Feature](https://en.wikipedia.org/wiki/Feature_(machine_learning)) article on Wikipedia.</span></span>

## <a name="feature-engineering"></a><span data-ttu-id="bfe2c-136">Funkce inženýrství</span><span class="sxs-lookup"><span data-stu-id="bfe2c-136">Feature engineering</span></span>

<span data-ttu-id="bfe2c-137">Funkce inženýrství je proces, který zahrnuje definování sady [funkce](#feature) a vývoji softwaru, který vytváří vektory funkce z dostupných jevu dat, tedy funkce extrakce.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-137">Feature engineering is the process that involves defining a set of [features](#feature) and developing software that produces feature vectors from available phenomenon data, i.e., feature extraction.</span></span> <span data-ttu-id="bfe2c-138">Další informace najdete v tématu [konstruování](https://en.wikipedia.org/wiki/Feature_engineering) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-138">For more information, see the [Feature engineering](https://en.wikipedia.org/wiki/Feature_engineering) article on Wikipedia.</span></span>

## <a name="f-score"></a><span data-ttu-id="bfe2c-139">F – score</span><span class="sxs-lookup"><span data-stu-id="bfe2c-139">F-score</span></span>

<span data-ttu-id="bfe2c-140">V [klasifikace](#classification), vyhodnocení metrika, který vyrovnává [přesnost](#precision) a [odvolání](#recall).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-140">In [classification](#classification), an evaluation metric that balances [precision](#precision) and [recall](#recall).</span></span>

<span data-ttu-id="bfe2c-141">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-141">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.F1Score?displayProperty=nameWithType>.</span></span>

## <a name="hyperparameter"></a><span data-ttu-id="bfe2c-142">Hyperparameter</span><span class="sxs-lookup"><span data-stu-id="bfe2c-142">Hyperparameter</span></span>

<span data-ttu-id="bfe2c-143">Parametr algoritmu strojového učení.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-143">A parameter of a machine learning algorithm.</span></span> <span data-ttu-id="bfe2c-144">Mezi příklady patří počet stromy další v doménové struktuře rozhodnutí nebo velikost kroku v algoritmus klesání přechodu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-144">Examples include the number of trees to learn in a decision forest or the step size in a gradient descent algorithm.</span></span> <span data-ttu-id="bfe2c-145">Hodnoty z *Hyperparameters* jsou nastavené před tréninku modelu a řídit proces hledání parametry funkce předpovědi, například porovnání body v rozhodovacím stromu nebo vah ve model lineární regrese .</span><span class="sxs-lookup"><span data-stu-id="bfe2c-145">Values of *Hyperparameters* are set before training the model and govern the process of finding the parameters of the prediction function, for example, the comparison points in a decision tree or the weights in a linear regression model.</span></span> <span data-ttu-id="bfe2c-146">Další informace najdete v tématu [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-146">For more information, see the [Hyperparameter](https://en.wikipedia.org/wiki/Hyperparameter_(machine_learning)) article on Wikipedia.</span></span>

## <a name="label"></a><span data-ttu-id="bfe2c-147">Popisek</span><span class="sxs-lookup"><span data-stu-id="bfe2c-147">Label</span></span>

<span data-ttu-id="bfe2c-148">Elementu, který chcete předpovědět s model strojového učení.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-148">The element to be predicted with the machine learning model.</span></span> <span data-ttu-id="bfe2c-149">Například se druh pes nebo budoucí uložených cena.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-149">For example, the breed of dog or a future stock price.</span></span>

## <a name="log-loss"></a><span data-ttu-id="bfe2c-150">Ztráta protokolu</span><span class="sxs-lookup"><span data-stu-id="bfe2c-150">Log loss</span></span>

<span data-ttu-id="bfe2c-151">V [klasifikace](#classification), metriku hodnocení, která charakterizuje přesnost třídění.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-151">In [classification](#classification), an evaluation metric that characterizes the accuracy of a classifier.</span></span> <span data-ttu-id="bfe2c-152">Menší ztrátě protokolu je, tím přesnější třídění.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-152">The smaller log loss is, the more accurate a classifier is.</span></span>

<span data-ttu-id="bfe2c-153">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-153">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.LogLoss?displayProperty=nameWithType>.</span></span>

## <a name="mean-absolute-error-mae"></a><span data-ttu-id="bfe2c-154">Střední absolutní chyba (MAE)</span><span class="sxs-lookup"><span data-stu-id="bfe2c-154">Mean absolute error (MAE)</span></span>

<span data-ttu-id="bfe2c-155">V [regrese](#regression), metriku hodnocení, která je průměr všech modelu chyb, kde chybu modelu je vzdálenost mezi předpokládaných [popisek](#label) hodnota a hodnota správný popisek.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-155">In [regression](#regression), an evaluation metric that is the average of all the model errors, where model error is the distance between the predicted [label](#label) value and the correct label value.</span></span>

<span data-ttu-id="bfe2c-156">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-156">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.L1?displayProperty=nameWithType>.</span></span>

## <a name="model"></a><span data-ttu-id="bfe2c-157">Model</span><span class="sxs-lookup"><span data-stu-id="bfe2c-157">Model</span></span>

<span data-ttu-id="bfe2c-158">Obvyklým parametry pro funkci předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-158">Traditionally, the parameters for the prediction function.</span></span> <span data-ttu-id="bfe2c-159">Například vah ve model lineární regrese nebo body rozdělení v rozhodovacím stromu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-159">For example, the weights in a linear regression model or the split points in a decision tree.</span></span> <span data-ttu-id="bfe2c-160">V ML.NET, model obsahuje všechny informace potřebné k předpovědi [popisek](#label) objektu domény (například obrázek nebo text).</span><span class="sxs-lookup"><span data-stu-id="bfe2c-160">In ML.NET, a model contains all the information necessary to predict the [label](#label) of a domain object (for example, image or text).</span></span> <span data-ttu-id="bfe2c-161">To znamená, že ML.NET modely zahrnout featurization kroky, které jsou nezbytné, a také parametry pro funkci předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-161">This means that ML.NET models include the featurization steps necessary as well as the parameters for the prediction function.</span></span>

## <a name="multiclass-classification"></a><span data-ttu-id="bfe2c-162">více třídami klasifikace</span><span class="sxs-lookup"><span data-stu-id="bfe2c-162">Multiclass classification</span></span>

<span data-ttu-id="bfe2c-163">A [klasifikace](#classification) případ where [popisek](#label) je jedním z tři nebo více tříd.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-163">A [classification](#classification) case where the [label](#label) is one out of three or more classes.</span></span> <span data-ttu-id="bfe2c-164">Další informace najdete v tématu [více třídami klasifikace](https://en.wikipedia.org/wiki/Multiclass_classification) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-164">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

## <a name="n-gram"></a><span data-ttu-id="bfe2c-165">N-gram</span><span class="sxs-lookup"><span data-stu-id="bfe2c-165">N-gram</span></span>

<span data-ttu-id="bfe2c-166">Funkce extrakce schéma pro data textu: žádné pořadí N slova se změní [funkce](#feature) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-166">A feature extraction scheme for text data: any sequence of N words turns into a [feature](#feature) value.</span></span>

## <a name="numerical-feature-vector"></a><span data-ttu-id="bfe2c-167">Numerické funkce vector</span><span class="sxs-lookup"><span data-stu-id="bfe2c-167">Numerical feature vector</span></span>

<span data-ttu-id="bfe2c-168">A [funkce](#feature) vektor, který se skládá pouze z číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-168">A [feature](#feature) vector consisting only of numerical values.</span></span> <span data-ttu-id="bfe2c-169">Toto je podobná `double[]`.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-169">This is similar to `double[]`.</span></span>

## <a name="pipeline"></a><span data-ttu-id="bfe2c-170">Kanál</span><span class="sxs-lookup"><span data-stu-id="bfe2c-170">Pipeline</span></span>

<span data-ttu-id="bfe2c-171">Všechny operace, je potřeba podle modelu pro datové sady.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-171">All of the operations needed to fit a model to a data set.</span></span> <span data-ttu-id="bfe2c-172">Kanál se skládá z importu dat, transformaci, featurization a učení kroky.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-172">A pipeline consists of data import, transformation, featurization, and learning steps.</span></span> <span data-ttu-id="bfe2c-173">Jakmile je vycvičena kanál, změní se do modelu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-173">Once a pipeline is trained, it turns into a model.</span></span>

## <a name="precision"></a><span data-ttu-id="bfe2c-174">Přesnost</span><span class="sxs-lookup"><span data-stu-id="bfe2c-174">Precision</span></span>

<span data-ttu-id="bfe2c-175">V [klasifikace](#classification), přesnost pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek předpovědět jako náležící k třídě.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-175">In [classification](#classification), the precision for a class is the number of items correctly predicted as belonging to that class divided by the total number of items predicted as belonging to the class.</span></span>

<span data-ttu-id="bfe2c-176">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-176">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativePrecision?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositivePrecision?displayProperty=nameWithType>.</span></span>

## <a name="recall"></a><span data-ttu-id="bfe2c-177">Odvolat</span><span class="sxs-lookup"><span data-stu-id="bfe2c-177">Recall</span></span>

<span data-ttu-id="bfe2c-178">V [klasifikace](#classification), odvolání pro třídu je počet položek správně předpovědět jako patřící do této třídy dělený celkový počet položek, které ve skutečnosti patří do třídy.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-178">In [classification](#classification), the recall for a class is the number of items correctly predicted as belonging to that class divided by the total number of items that actually belong to the class.</span></span>

<span data-ttu-id="bfe2c-179">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-179">Related ML.NET API: <xref:Microsoft.ML.Models.BinaryClassificationMetrics.NegativeRecall?displayProperty=nameWithType>, <xref:Microsoft.ML.Models.BinaryClassificationMetrics.PositiveRecall?displayProperty=nameWithType>.</span></span>

## <a name="regression"></a><span data-ttu-id="bfe2c-180">Regrese</span><span class="sxs-lookup"><span data-stu-id="bfe2c-180">Regression</span></span>

<span data-ttu-id="bfe2c-181">A [počítač učení se supervizí](#supervised-machine-learning) úloh, kde výstup je skutečné hodnoty, například, double.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-181">A [supervised machine learning](#supervised-machine-learning) task where the output is a real value, for example, double.</span></span> <span data-ttu-id="bfe2c-182">Mezi příklady patří predikci uložených ceny.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-182">Examples include predicting stock prices.</span></span>

## <a name="relative-absolute-error"></a><span data-ttu-id="bfe2c-183">Relativní absolutní chyba</span><span class="sxs-lookup"><span data-stu-id="bfe2c-183">Relative absolute error</span></span>

<span data-ttu-id="bfe2c-184">V [regrese](#regression), metriku hodnocení, která je součet hodnot všech absolutních chyb dělený součet vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte popisek hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-184">In [regression](#regression), an evaluation metric that is the sum of all absolute errors divided by the sum of distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="relative-squared-error"></a><span data-ttu-id="bfe2c-185">Relativní kvadratická chyba</span><span class="sxs-lookup"><span data-stu-id="bfe2c-185">Relative squared error</span></span>

<span data-ttu-id="bfe2c-186">V [regrese](#regression), metriku hodnocení, která je součet všech spolehlivosti absolutních chyb a součtu kvadratických vzdálenosti mezi správné [popisek](#label) hodnotami a průměrem všech opravte popisek hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-186">In [regression](#regression), an evaluation metric that is the sum of all squared absolute errors divided by the sum of squared distances between correct [label](#label) values and the average of all correct label values.</span></span>

## <a name="root-of-mean-squared-error-rmse"></a><span data-ttu-id="bfe2c-187">Kořenové střední spolehlivosti chyby (RMSE)</span><span class="sxs-lookup"><span data-stu-id="bfe2c-187">Root of mean squared error (RMSE)</span></span>

<span data-ttu-id="bfe2c-188">V [regrese](#regression), vyhodnocení metriky, která je druhá odmocnina průměru kvadratických chyb.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-188">In [regression](#regression), an evaluation metric that is the square root of the average of the squares of the errors.</span></span>

<span data-ttu-id="bfe2c-189">Rozhraní API související ML.NET: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-189">Related ML.NET API: <xref:Microsoft.ML.Models.RegressionMetrics.Rms?displayProperty=nameWithType>.</span></span>

## <a name="supervised-machine-learning"></a><span data-ttu-id="bfe2c-190">Strojového učení</span><span class="sxs-lookup"><span data-stu-id="bfe2c-190">Supervised machine learning</span></span>

<span data-ttu-id="bfe2c-191">Podtřídou třídy strojového učení, ve kterém požadované modelu předpovídá popisek pro ještě neviditelný data.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-191">A subclass of machine learning in which a desired model predicts the label for yet-unseen data.</span></span> <span data-ttu-id="bfe2c-192">Mezi příklady patří klasifikaci, regresi a strukturovaných předpovědi.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-192">Examples include classification, regression, and structured prediction.</span></span> <span data-ttu-id="bfe2c-193">Další informace najdete v tématu [učení se Supervizí](https://en.wikipedia.org/wiki/Supervised_learning) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-193">For more information, see the  [Supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) article on Wikipedia.</span></span>

## <a name="training"></a><span data-ttu-id="bfe2c-194">Školení</span><span class="sxs-lookup"><span data-stu-id="bfe2c-194">Training</span></span>

<span data-ttu-id="bfe2c-195">Proces identifikace [modelu](#model) pro danou trénovací datové sady.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-195">The process of identifying a [model](#model) for a given training data set.</span></span> <span data-ttu-id="bfe2c-196">Pro model lineární to znamená, že hledání vah.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-196">For a linear model, this means finding the weights.</span></span> <span data-ttu-id="bfe2c-197">Pro strom zahrnuje identifikace body rozdělení.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-197">For a tree, it involves the identifying the split points.</span></span>

## <a name="transform"></a><span data-ttu-id="bfe2c-198">Transformace</span><span class="sxs-lookup"><span data-stu-id="bfe2c-198">Transform</span></span>

<span data-ttu-id="bfe2c-199">A [kanálu](#pipeline) komponenty, která transformuje data.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-199">A [pipeline](#pipeline) component that transforms data.</span></span> <span data-ttu-id="bfe2c-200">Například z text vector čísel.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-200">For example, from text to vector of numbers.</span></span>

## <a name="unsupervised-machine-learning"></a><span data-ttu-id="bfe2c-201">Bez dohledu machine learning</span><span class="sxs-lookup"><span data-stu-id="bfe2c-201">Unsupervised machine learning</span></span>

<span data-ttu-id="bfe2c-202">Podtřídou třídy strojového učení, ve kterém požadované modelu najde struktura skrytá (nebo latentní) v datech.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-202">A subclass of machine learning in which a desired model finds hidden (or latent) structure in data.</span></span> <span data-ttu-id="bfe2c-203">Mezi příklady patří clustering, tématu modelování a snížení dimenzionalitu.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-203">Examples include clustering, topic modeling, and dimensionality reduction.</span></span> <span data-ttu-id="bfe2c-204">Další informace najdete v tématu [Supervize](https://en.wikipedia.org/wiki/Unsupervised_learning) článku na webu Wikipedia.</span><span class="sxs-lookup"><span data-stu-id="bfe2c-204">For more information, see the [Unsupervised learning](https://en.wikipedia.org/wiki/Unsupervised_learning) article on Wikipedia.</span></span>
