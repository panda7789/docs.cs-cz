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
1. S grafickým uživatelským rozhraním, pomocí Tvůrce modelu ML.NET
