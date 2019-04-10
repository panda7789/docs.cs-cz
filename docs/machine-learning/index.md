---
title: Průvodce ML.NET obsahem
description: Zjistěte, jak vytvářet vlastní řešení AI a integrovat do aplikací .NET pomocí ML.NET.
ms.date: 04/05/2019
ms.custom: seodec18
ms.openlocfilehash: de681daea5a29a121d350271ced4ccc2c0b1b533
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231328"
---
# <a name="mlnet-content-guide"></a><span data-ttu-id="5ea6a-103">Průvodce ML.NET obsahem</span><span class="sxs-lookup"><span data-stu-id="5ea6a-103">ML.NET Content Guide</span></span>

<span data-ttu-id="5ea6a-104">Tato příručka vysvětluje základní koncepty a poskytuje podrobné pokyny a referenční dokumentace rozhraní API pro práci s ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-104">This guide explains basic concepts and provides tutorials and an API reference for working with ML.NET.</span></span>

> [!NOTE]
> <span data-ttu-id="5ea6a-105">Tato dokumentace odkazuje na ML.NET, která je aktuálně ve verzi Preview.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-105">This documentation refers to ML.NET, which is currently in Preview.</span></span> <span data-ttu-id="5ea6a-106">Materiál může být mohou změnit.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-106">Material may be subject to change.</span></span> <span data-ttu-id="5ea6a-107">Další informace najdete v tématu [ML.NET ÚVOD](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-107">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

## <a name="get-started"></a><span data-ttu-id="5ea6a-108">Začínáme</span><span class="sxs-lookup"><span data-stu-id="5ea6a-108">Get started</span></span>

<span data-ttu-id="5ea6a-109">K instalaci a začněte sestavovat ML.NET, postupujte [kurz Začínáme](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-109">To install and start building in ML.NET, follow the [Get started tutorial](https://www.microsoft.com/net/learn/machinelearning-ai/ml-dotnet-get-started-tutorial).</span></span>

<span data-ttu-id="5ea6a-110">Další informace o ML.NET najdete v tématu [novinky ML.NET?](what-is-mldotnet.md)</span><span class="sxs-lookup"><span data-stu-id="5ea6a-110">To learn about ML.NET, see [What is ML.NET?](what-is-mldotnet.md)</span></span>

<span data-ttu-id="5ea6a-111">Základní informace najdete v tématu [základní koncepty k tréninku modelu v ML.NET](basic-concepts-model-training-in-mldotnet.md).</span><span class="sxs-lookup"><span data-stu-id="5ea6a-111">To understand basics, see [Basic concepts for model training in ML.NET](basic-concepts-model-training-in-mldotnet.md).</span></span>

## <a name="tutorials"></a><span data-ttu-id="5ea6a-112">Kurzy</span><span class="sxs-lookup"><span data-stu-id="5ea6a-112">Tutorials</span></span>

<span data-ttu-id="5ea6a-113">[Analýza sentimentu pomocí binární klasifikační model](./tutorials/sentiment-analysis.md) se dozvíte, jak vytvořit aplikaci, která určuje, zda je pozitivní nebo negativní zabarvení.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-113">[Analyze sentiment using a binary classification model](./tutorials/sentiment-analysis.md) shows you how to build an app that determines whether sentiment is positive or negative.</span></span>

<span data-ttu-id="5ea6a-114">[Klasifikaci problémy s úložištěm GitHub pomocí klasifikace víc tříd modelu](./tutorials/github-issue-classification.md) ukazuje, jak vytvořit aplikaci, která určuje popisek oblasti pro problém na Githubu.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-114">[Classify GitHub issues using a multiclass classification model](./tutorials/github-issue-classification.md) shows you how to build an app that determines the Area label for a GitHub issue.</span></span>

<span data-ttu-id="5ea6a-115">[Předvídání cen pomocí regresní model](./tutorials/taxi-fare.md) se dozvíte, jak vytvořit prediktivní aplikaci, která používá mnoho faktorů, z historických dat. Chcete-li zjistit odpověď.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-115">[Predict prices using a regression model](./tutorials/taxi-fare.md) shows you how to build a predictive app that uses many factors from historical data to determine the answer.</span></span>

<span data-ttu-id="5ea6a-116">[Klasifikace iris květin funkcemi](./tutorials/iris-clustering.md) se dozvíte, jak analyzovat datové sady iris pomocí model clusteringu.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-116">[Classify iris flowers by features](./tutorials/iris-clustering.md) shows you how to use a clustering model to analyze the iris data set.</span></span>

<span data-ttu-id="5ea6a-117">[Vytvoření doporučené video s ML.NET](./tutorials/movie-recommmendation.md) se dozvíte, jak vytvořit aplikaci doporučení pro doporučování filmů pro uživatele na základě jejich historie.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-117">[Create a Movie Recommender with ML.NET](./tutorials/movie-recommmendation.md) shows you how to build a recommendation app to recommend movies to users based on their history.</span></span>

<span data-ttu-id="5ea6a-118">[Sestavení klasifikátoru vlastní image ML.NET s TensorFlow](./tutorials/image-classification.md): ukazuje, jak přeučování existující model Tensorflow k vytvoření vlastní image třídění pomocí ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-118">[Build an ML.NET custom image classifier with TensorFlow](./tutorials/image-classification.md): demonstrates how to retrain an existing Tensorflow model to create a custom image classifier using ML.NET.</span></span>

## <a name="how-to-guide"></a><span data-ttu-id="5ea6a-119">Průvodce postupy</span><span class="sxs-lookup"><span data-stu-id="5ea6a-119">How to guide</span></span>

<span data-ttu-id="5ea6a-120">[Sestavení aplikace herní seznamu nahoru shoda s pravděpodobnostní programování a Infer.NET](./how-to-guides/matchup-app-infer-net.md) se dozvíte, jak vytvořit zjednodušenou verzi shoda nahoru aplikaci jako se zobrazí ve hry pro Xbox.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-120">[Build a game match-up list app with Infer.NET and probabilistic programming](./how-to-guides/matchup-app-infer-net.md) shows you how to build a simplified version of a match-up app like you'd see in an Xbox game.</span></span>

## <a name="resources"></a><span data-ttu-id="5ea6a-121">Prostředky</span><span class="sxs-lookup"><span data-stu-id="5ea6a-121">Resources</span></span>

<span data-ttu-id="5ea6a-122">[Machine learning Glosář](./resources/glossary.md) definuje klíčová terminologie.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-122">[Machine learning glossary](./resources/glossary.md) defines key terminology.</span></span>

<span data-ttu-id="5ea6a-123">[Služby Machine learning úlohy](./resources/tasks.md) popisuje úlohy, jako je například klasifikace a detekce anomálií.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-123">[Machine learning tasks](./resources/tasks.md) describes tasks, such as classification and anomaly detection.</span></span> 

<span data-ttu-id="5ea6a-124">[Transformace dat](./resources/transforms.md) popisuje možnosti přípravy dat v ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-124">[Data transforms](./resources/transforms.md) describes data preparation capabilities in ML.NET.</span></span>

## <a name="api-reference"></a><span data-ttu-id="5ea6a-125">referenční dokumentace k rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5ea6a-125">API reference</span></span>

<span data-ttu-id="5ea6a-126">[Reference k rozhraní API ML.NET](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) popisuje škálu rozhraní API, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5ea6a-126">[ML.NET API Reference](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) describes the breadth of APIs available.</span></span>
