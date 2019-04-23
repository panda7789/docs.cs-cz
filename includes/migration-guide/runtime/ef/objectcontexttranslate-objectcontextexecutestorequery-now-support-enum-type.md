---
ms.openlocfilehash: 1d2d6133683360b97569e49402e7c8c4d182b65d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803659"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext.Translate a ObjectContext.ExecuteStoreQuery teď podporují typ výčtu

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.0, obecný parametr <code>T</code> z <code>ObjectContext.Translate</code> a <code>ObjectContext.ExecuteStoreQuery</code> metody nemůže být výčet. Tento scénář je nyní podporován.|
|Doporučení|Pokud přeložit nebo ExecuteStoreQuery byla volána pro typ výčtu v rozhraní .NET Framework 4.0, byl vrácen '0'. Pokud toto chování je žádoucí, měl by být volání nahrazen – konstanta 0 (nebo ekvivalentní výčtu je).|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
