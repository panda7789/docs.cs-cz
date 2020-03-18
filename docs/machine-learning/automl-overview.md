---
title: Automatizované strojové učení s ML.NET
description: Přehled automatického výběru a školení modelů
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: acd6cae71d2d5d79209a77d34175e7f1b3c1ee35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849351"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="312ef-103">Automatizované strojové učení s ML.NET</span><span class="sxs-lookup"><span data-stu-id="312ef-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="312ef-104">Automatizované strojové učení je funkce ML.NET, která provádí automatický výběr modelu a školení.</span><span class="sxs-lookup"><span data-stu-id="312ef-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="312ef-105">Zadáte úlohu strojového učení a zadáte datovou sadu a automatizovaná ml vybere model s nejlepšími metrikami.</span><span class="sxs-lookup"><span data-stu-id="312ef-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="312ef-106">To výstupy:</span><span class="sxs-lookup"><span data-stu-id="312ef-106">It outputs:</span></span>

- <span data-ttu-id="312ef-107">soubor modelu, který lze načíst do aplikace předpověď</span><span class="sxs-lookup"><span data-stu-id="312ef-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="312ef-108">kód aplikace, aby se předpovědi</span><span class="sxs-lookup"><span data-stu-id="312ef-108">application code to make predictions</span></span>
- <span data-ttu-id="312ef-109">zdrojový kód používaný pro výběr funkcí a trénování modelu (pro pochopení modelu)</span><span class="sxs-lookup"><span data-stu-id="312ef-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="312ef-110">Tato funkce je v současné době ve verzi Preview a materiál se může změnit.</span><span class="sxs-lookup"><span data-stu-id="312ef-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="312ef-111">Automatizované ML je aktuálně omezena na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace více tříd a regrese.</span><span class="sxs-lookup"><span data-stu-id="312ef-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="312ef-112">Ostatní úlohy strojového učení budou podporovány v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="312ef-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="312ef-113">Automatické ml lze používat třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="312ef-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="312ef-114">S grafickým uživatelským rozhraním, s [ML.NET Model Builder](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="312ef-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="312ef-115">Na příkazovém řádku s [ML.NET příkazovým příkazem](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="312ef-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="312ef-116">Prostřednictvím aplikace s [automatizovaným ROZHRANÍM ML API](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="312ef-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
