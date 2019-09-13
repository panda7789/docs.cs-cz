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
# <a name="automated-machine-learning-with-mlnet"></a>Automatizované Machine Learning s ML.NET

Automatizované Machine Learning je funkce ML.NET, která provádí automatický výběr modelů a školení. Můžete zadat úlohu strojového učení a zadat datovou sadu a automatizovanou ML si vyberou model s nejlepšími metrikami. Výstupy IT:

- soubor modelu, který lze načíst do aplikace předpovědi
- kód aplikace pro vytvoření předpovědi
- zdrojový kód, který se používá pro výběr funkcí a pro školení modelů (pro pochopení modelu)

> [!NOTE]
> Tato funkce je aktuálně ve verzi Preview a může se stát, že se změní materiál. 

Automatizované ML je aktuálně omezené na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace s více třídami a regrese. Ostatní úkoly strojového učení budou v budoucích vydáních podporovány.

Existují tři způsoby použití automatizovaného ML:

1. S grafickým uživatelským rozhraním pomocí [Tvůrce modelů ml.NET](automate-training-with-model-builder.md)
1. V příkazovém řádku s rozhraním [CLI ml.NET](automate-training-with-cli.md)
1. Přes aplikaci s [rozhraním API automatizovaného ml](how-to-guides/how-to-use-the-automl-api.md)
