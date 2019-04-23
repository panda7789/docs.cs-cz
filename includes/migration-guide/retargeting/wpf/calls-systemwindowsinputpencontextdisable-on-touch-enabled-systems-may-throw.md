---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982144"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Volání System.Windows.Input.PenContext.Disable systémech s dotykovým ovládáním může vyvolat ArgumentException

|   |   |
|---|---|
|Podrobnosti|Za určitých okolností volání vnitřní <strong>System.Windows.Intput.PenContext.Disable</strong> může vyvolat metodu na systémy s dotykovým ovládáním neošetřenou <code>T:System.ArgumentException</code> kvůli vícenásobnému přístupu.|
|Doporučení|Tento problém byl vyřešen v rozhraní .NET Framework 4.7. Pokud chcete zabránit výjimku, upgradujte na verzi rozhraní .NET Framework počínaje .NET Framework 4.7.|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Změna cílení|
