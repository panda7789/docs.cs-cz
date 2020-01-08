---
title: Automatizované Machine Learning s ML.NET
description: Přehled automatického výběru modelu a školení
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 251ca50f062f415ac4dfeda243eb746e9744b6f4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345185"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="2336f-103">Automatizované Machine Learning s ML.NET</span><span class="sxs-lookup"><span data-stu-id="2336f-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="2336f-104">Automatizované Machine Learning je funkce ML.NET, která provádí automatický výběr modelů a školení.</span><span class="sxs-lookup"><span data-stu-id="2336f-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="2336f-105">Můžete zadat úlohu strojového učení a zadat datovou sadu a automatizovanou ML si vyberou model s nejlepšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="2336f-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="2336f-106">Výstupy IT:</span><span class="sxs-lookup"><span data-stu-id="2336f-106">It outputs:</span></span>

- <span data-ttu-id="2336f-107">soubor modelu, který lze načíst do aplikace předpovědi</span><span class="sxs-lookup"><span data-stu-id="2336f-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="2336f-108">kód aplikace pro vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="2336f-108">application code to make predictions</span></span>
- <span data-ttu-id="2336f-109">zdrojový kód, který se používá pro výběr funkcí a pro školení modelů (pro pochopení modelu)</span><span class="sxs-lookup"><span data-stu-id="2336f-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="2336f-110">Tato funkce je aktuálně ve verzi Preview a může se stát, že se změní materiál.</span><span class="sxs-lookup"><span data-stu-id="2336f-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="2336f-111">Automatizované ML je aktuálně omezené na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace s více třídami a regrese.</span><span class="sxs-lookup"><span data-stu-id="2336f-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="2336f-112">Ostatní úkoly strojového učení budou v budoucích vydáních podporovány.</span><span class="sxs-lookup"><span data-stu-id="2336f-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="2336f-113">Existují tři způsoby použití automatizovaného ML:</span><span class="sxs-lookup"><span data-stu-id="2336f-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="2336f-114">S grafickým uživatelským rozhraním pomocí [Tvůrce modelů ml.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="2336f-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="2336f-115">V příkazovém řádku s rozhraním [CLI ml.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="2336f-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="2336f-116">Přes aplikaci s [rozhraním API automatizovaného ml](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="2336f-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
