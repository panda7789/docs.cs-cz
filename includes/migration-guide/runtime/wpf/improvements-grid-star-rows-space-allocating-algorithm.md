---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237621"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Vylepšení políčku mřížky řádků hvězdičku přidělování algoritmus

|   |   |
|---|---|
|Podrobnosti|Oprava chyby v [algoritmus pro přidělování velikostí, které](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) v <xref:System.Windows.Controls.Grid> zavedena v rozhraní .NET Framework 4.7.  V některých případech, jako je například mřížka s <code>Height=&quot;Auto&quot;</code> obsahující prázdné řádky, řádky uspořádaly nesprávné pozici pravděpodobně mimo mřížky úplně se vynechá.|
|Doporučení|Aby aplikace využívat tyto změny musí běžet na 4.8 rozhraní .NET Framework nebo novější.|
|Scope|Hlavní|
|Version|4.8|
|type|Modul runtime|
