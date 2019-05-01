---
ms.openlocfilehash: cbd599f7467c3b360bbe1c76a65abfdb840a1530
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088466"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF vytvoří wisptis.exe proces, který může zablokovat myši

|   |   |
|---|---|
|Podrobnosti|Problém byl zaveden ve verzi 4.5.2, který způsobí, že <code>wisptis.exe</code> k se vytvoří podřízený proces, který může zablokovat vstup z myši.|
|Doporučení|Oprava tohoto problému je k dispozici v servisní verze rozhraní .NET Framework 4.5.2 (kumulativní opravu hotfix 3026376) nebo upgradem na rozhraní .NET Framework 4.6|
|Rozsah|Hlavní|
|Version|4.5.2|
|Type|Modul runtime|
