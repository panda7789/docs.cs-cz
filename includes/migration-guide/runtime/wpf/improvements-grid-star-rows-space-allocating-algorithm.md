---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802692"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus

|   |   |
|---|---|
|Podrobnosti|Oprava chyby v [algoritmus pro přidělování velikostí, které ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.  V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.|
|Doporučení|Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.|
|Scope|Hlavní|
|Version|4.8|
|type|Modul runtime|

