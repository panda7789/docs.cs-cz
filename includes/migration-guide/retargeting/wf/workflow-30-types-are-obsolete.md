---
ms.openlocfilehash: 358103d5816eb61c88738e9626fb02c563b507f8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617247"
---
### <a name="workflow-30-types-are-obsolete"></a>Typy WorkFlow 3.0 jsou zastaralé

#### <a name="details"></a>Podrobnosti

Rozhraní API modelu Windows Workflow Foundation (WWF) 3.0 (tj. rozhraní z oboru názvů System.Workflow) jsou už zastaralá.

#### <a name="suggestion"></a>Návrh

Je vhodné místo nich používat nová rozhraní API WWF 4.0 (z oboru názvů System.Activities). Příklad použití nových rozhraní API najdete [tady](~/docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md) a další pokyny jsou k dispozici [tady](https://docs.microsoft.com/archive/blogs/workflowteam/wf3-types-marked-obsolete-in-net-4-5). Rozhraní API WWF 3.0 se stále podporují, můžete je tedy případně použít. Upozornění na čas sestavení se vyhnete tím, že ho potlačíte nebo použijete starší kompilátor.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Hlavní       |
| Verze | 4.5         |
| Typ    | Změna cílení |
