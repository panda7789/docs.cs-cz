---
title: Automatizované Machine Learning s ML.NET
description: Přehled automatického výběru modelu a školení
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: da2d764e678debc78a25faeb8e48facb44fc4021
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929426"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="d0110-103">Automatizované Machine Learning s ML.NET</span><span class="sxs-lookup"><span data-stu-id="d0110-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="d0110-104">Automatizované Machine Learning je funkce ML.NET, která provádí automatický výběr modelů a školení.</span><span class="sxs-lookup"><span data-stu-id="d0110-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="d0110-105">Můžete zadat úlohu strojového učení a zadat datovou sadu a automatizovanou ML si vyberou model s nejlepšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="d0110-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="d0110-106">Výstupy IT:</span><span class="sxs-lookup"><span data-stu-id="d0110-106">It outputs:</span></span>

- <span data-ttu-id="d0110-107">soubor modelu, který lze načíst do aplikace předpovědi</span><span class="sxs-lookup"><span data-stu-id="d0110-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="d0110-108">kód aplikace pro vytvoření předpovědi</span><span class="sxs-lookup"><span data-stu-id="d0110-108">application code to make predictions</span></span>
- <span data-ttu-id="d0110-109">zdrojový kód, který se používá pro výběr funkcí a pro školení modelů (pro pochopení modelu)</span><span class="sxs-lookup"><span data-stu-id="d0110-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="d0110-110">Tato funkce je aktuálně ve verzi Preview a může se stát, že se změní materiál.</span><span class="sxs-lookup"><span data-stu-id="d0110-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="d0110-111">Automatizované ML je aktuálně omezené na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace s více třídami a regrese.</span><span class="sxs-lookup"><span data-stu-id="d0110-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="d0110-112">Ostatní úkoly strojového učení budou v budoucích vydáních podporovány.</span><span class="sxs-lookup"><span data-stu-id="d0110-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="d0110-113">Existují tři způsoby použití automatizovaného ML:</span><span class="sxs-lookup"><span data-stu-id="d0110-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="d0110-114">S grafickým uživatelským rozhraním pomocí [Tvůrce modelů ml.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="d0110-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="d0110-115">V příkazovém řádku s rozhraním [CLI ml.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="d0110-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="d0110-116">Přes aplikaci s [rozhraním API automatizovaného ml](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="d0110-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
