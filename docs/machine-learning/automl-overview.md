---
title: Automatizované strojového učení s ML.NET
description: Přehled automatického modelu výběru a školení
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: e6654718f174c9d8b628b05d85d74952c222eb66
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452725"
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
1. Na příkazovém řádku se [ML.NET rozhraní příkazového řádku](automate-training-with-cli.md)
1. Prostřednictvím aplikace se [automatizované ML API](how-to-guides/how-to-use-the-automl-api.md)
1. S grafickým uživatelským rozhraním se Tvůrce modelu ML.NET
