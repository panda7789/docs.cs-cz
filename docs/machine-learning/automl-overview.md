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
# <a name="automated-machine-learning-with-mlnet"></a>Automatizované strojové učení s ML.NET

Automatizované strojové učení je funkce ML.NET, která provádí automatický výběr modelu a školení. Zadáte úlohu strojového učení a zadáte datovou sadu a automatizovaná ml vybere model s nejlepšími metrikami. To výstupy:

- soubor modelu, který lze načíst do aplikace předpověď
- kód aplikace, aby se předpovědi
- zdrojový kód používaný pro výběr funkcí a trénování modelu (pro pochopení modelu)

> [!NOTE]
> Tato funkce je v současné době ve verzi Preview a materiál se může změnit.

Automatizované ML je aktuálně omezena na [úlohy](resources/tasks.md) strojového učení binární klasifikace, klasifikace více tříd a regrese. Ostatní úlohy strojového učení budou podporovány v budoucích verzích.

Automatické ml lze používat třemi způsoby:

1. S grafickým uživatelským rozhraním, s [ML.NET Model Builder](automate-training-with-model-builder.md)
1. Na příkazovém řádku s [ML.NET příkazovým příkazem](automate-training-with-cli.md)
1. Prostřednictvím aplikace s [automatizovaným ROZHRANÍM ML API](how-to-guides/how-to-use-the-automl-api.md)
