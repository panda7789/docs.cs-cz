---
title: Automatizované strojového učení s ML.NET
description: Přehled automatického modelu výběru a školení
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 39e454d67f60280c6a43e3b80d788d873345ab77
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307379"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="4e166-103">Automatizované strojového učení s ML.NET</span><span class="sxs-lookup"><span data-stu-id="4e166-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="4e166-104">Automatizované machine learning je funkce ML.NET, který provádí výběr automatické modelu a školení.</span><span class="sxs-lookup"><span data-stu-id="4e166-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="4e166-105">Zadejte úlohu, machine learning a zadejte datovou sadu a automatizované ML zvolí model s nejlepší metriky.</span><span class="sxs-lookup"><span data-stu-id="4e166-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="4e166-106">Výstupu:</span><span class="sxs-lookup"><span data-stu-id="4e166-106">It outputs:</span></span>
- <span data-ttu-id="4e166-107">Soubor modelu, který je možné načíst do vaší aplikace predikcí</span><span class="sxs-lookup"><span data-stu-id="4e166-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="4e166-108">kód aplikace k následné predikci</span><span class="sxs-lookup"><span data-stu-id="4e166-108">application code to make predictions</span></span>
- <span data-ttu-id="4e166-109">zdrojový kód pro výběr funkce a model školení (pro pochopení modelu)</span><span class="sxs-lookup"><span data-stu-id="4e166-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="4e166-110">Tato funkce je aktuálně ve verzi Preview a materiálu se můžou stát terčem změnit.</span><span class="sxs-lookup"><span data-stu-id="4e166-110">This feature is currently in Preview, and material may be subject to change.</span></span> 

<span data-ttu-id="4e166-111">Automatizované ML je aktuálně omezená, machine Learning [úlohy](resources/tasks.md) binární klasifikace, klasifikace víc tříd a regrese.</span><span class="sxs-lookup"><span data-stu-id="4e166-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="4e166-112">Strojové učení, které úkoly budou podporované v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="4e166-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="4e166-113">Existují tři způsoby, jak používat automatizované ML:</span><span class="sxs-lookup"><span data-stu-id="4e166-113">There are three ways to use automated ML:</span></span>
1. <span data-ttu-id="4e166-114">Na příkazovém řádku se [ML.NET rozhraní příkazového řádku](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="4e166-114">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="4e166-115">Prostřednictvím aplikace se [automatizované ML API](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="4e166-115">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
1. <span data-ttu-id="4e166-116">S grafickým uživatelským rozhraním, pomocí Tvůrce modelu ML.NET</span><span class="sxs-lookup"><span data-stu-id="4e166-116">With a graphical user interface, with the ML.NET Model Builder</span></span>
