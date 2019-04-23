---
ms.openlocfilehash: bd3b1cc6a98f01d8c40b4cd67002e79a2c4fe714
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982238"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus

|   |   |
|---|---|
|Podrobnosti|Oprava chyby v [algoritmus pro přidělování velikostí, které *-řádků](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.  V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.|
|Doporučení|Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.|
|Rozsah|Hlavní|
|Version|4.8|
|Type|Modul runtime|
