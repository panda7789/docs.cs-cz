---
ms.openlocfilehash: c9efbefc2bce9e21f328680795e72b62bfcd5cbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803724"
---
### <a name="enumerableemptytresult-always-returns-cached-instance"></a>Enumerable.Empty\<TResult > vždy vrátí v mezipaměti instance

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> vždy vrátí instanci interní mezipaměti <xref:System.Collections.Generic.IEnumerable%601>. Dříve <xref:System.Linq.Enumerable.Empty%60%601> by mezipaměti prázdná <xref:System.Collections.Generic.IEnumerable%601> během rozhraní API byla volána, to znamená, že v některé podmínky, ve kterém <xref:System.Linq.Enumerable.Empty%60%601> byla volána rychle a současně, různé instance daného typu může být vrácen pro různé volání ROZHRANÍ API.|
|Doporučení|Protože předchozí chování je Nedeterministický, kód je nepravděpodobné, že by na něm závisí. Ale v případě nepravděpodobné, že se porovnávají prázdný výčty a má být v některých případech nerovnost, by měl být vytvořen explicitní prázdná pole (<code>new T[0]</code>) namísto použití <xref:System.Linq.Enumerable.Empty%60%601>.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|
