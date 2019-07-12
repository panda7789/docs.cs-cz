---
ms.openlocfilehash: 0d8108ef1c5b815b42003c247b4ff39099b2361a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803250"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a>WPF vytvoří wisptis.exe proces, který může zablokovat myši

|   |   |
|---|---|
|Podrobnosti|Problém byl zaveden ve verzi 4.5.2, který způsobí, že <code>wisptis.exe</code> k se vytvoří podřízený proces, který může zablokovat vstup z myši.|
|Doporučení|Oprava tohoto problému je k dispozici v servisní verze rozhraní .NET Framework 4.5.2 (kumulativní opravu hotfix 3026376) nebo upgradem na rozhraní .NET Framework 4.6|
|Scope|Hlavní|
|Version|4.5.2|
|type|Modul runtime|

