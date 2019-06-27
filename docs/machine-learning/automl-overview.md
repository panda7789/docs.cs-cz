---
title: Automatizované strojového učení s ML.NET
description: Přehled automatického modelu výběru a školení
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e34694eedd06c0a3e3558c9137c6add9a7f802e4
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410524"
---
# <a name="automated-machine-learning-with-mlnet"></a>Automatizované strojového učení s ML.NET

Automatizované machine learning je funkce ML.NET, který provádí výběr automatické modelu a školení. Zadejte úlohu, machine learning a zadejte datovou sadu a automatizované ML zvolí model s nejlepší metriky. Výstupu:
- Soubor modelu, který je možné načíst do vaší aplikace predikcí
- kód aplikace k následné predikci
- zdrojový kód pro výběr funkce a model školení (pro pochopení modelu)

> [!NOTE]
> Tato funkce je aktuálně ve verzi Preview a materiálu se můžou stát terčem změnit. 

Automatizované ML je aktuálně omezená, machine Learning [úlohy](resources/tasks.md) binární klasifikace, klasifikace víc tříd a regrese. Strojové učení, které úkoly budou podporované v budoucích verzích.

Existují tři způsoby, jak používat automatizované ML:
1. S grafickým uživatelským rozhraním se [Tvůrce modelu ML.NET](automate-training-with-model-builder.md)
1. Na příkazovém řádku se [ML.NET rozhraní příkazového řádku](automate-training-with-cli.md)
1. Prostřednictvím aplikace se [automatizované ML API](how-to-guides/how-to-use-the-automl-api.md)
