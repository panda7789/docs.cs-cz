---
title: Automatizované Machine Learning s ML.NET
description: Přehled automatického výběru modelu a školení
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: c6c369dc0b0375f180d33d85ef320ddb24102f3e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740095"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="9a4fc-103">Automatizované Machine Learning s ML.NET</span><span class="sxs-lookup"><span data-stu-id="9a4fc-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="9a4fc-104">Automatizované Machine Learning je funkce ML.NET, která provádí automatický výběr modelů a školení.</span><span class="sxs-lookup"><span data-stu-id="9a4fc-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="9a4fc-105">Můžete zadat úlohu strojového učení a zadat datovou sadu a automatizovanou ML si vyberou model s nejlepšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="9a4fc-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="9a4fc-106">Výstupy IT:</span><span class="sxs-lookup"><span data-stu-id="9a4fc-106">It outputs:</span></span>

- <span data-ttu-id="9a4fc-107">soubor modelu, který lze načíst do aplikace předpovědi</span><span class="sxs-lookup"><span data-stu-id="9a4fc-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="9a4fc-108">kód aplikace pro vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="9a4fc-108">application code to make predictions</span></span>
- <span data-ttu-id="9a4fc-109">zdrojový kód, který se používá pro výběr funkcí a pro školení modelů (pro pochopení modelu)</span><span class="sxs-lookup"><span data-stu-id="9a4fc-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="9a4fc-110">Tato funkce je aktuálně ve verzi Preview a může se stát, že se změní materiál.</span><span class="sxs-lookup"><span data-stu-id="9a4fc-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="9a4fc-111">Automatizované ML je aktuálně omezené na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace s více třídami a regrese.</span><span class="sxs-lookup"><span data-stu-id="9a4fc-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="9a4fc-112">Ostatní úkoly strojového učení budou v budoucích vydáních podporovány.</span><span class="sxs-lookup"><span data-stu-id="9a4fc-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="9a4fc-113">Existují tři způsoby použití automatizovaného ML:</span><span class="sxs-lookup"><span data-stu-id="9a4fc-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="9a4fc-114">S grafickým uživatelským rozhraním pomocí [Tvůrce modelů ml.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="9a4fc-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="9a4fc-115">V příkazovém řádku s rozhraním [CLI ml.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="9a4fc-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="9a4fc-116">Přes aplikaci s [rozhraním API automatizovaného ml](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="9a4fc-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
