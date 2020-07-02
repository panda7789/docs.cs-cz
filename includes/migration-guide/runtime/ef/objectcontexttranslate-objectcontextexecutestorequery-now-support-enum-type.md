---
ms.openlocfilehash: 6af8e97423c04abca25feb8d77ea9ab6e198a4f0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620029"
---
### <a name="objectcontexttranslate-and-objectcontextexecutestorequery-now-support-enum-type"></a>ObjectContext. repřeklady a ObjectContext.ExecuteStoreQuery nyní podporují typ výčtu.

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,0 obecný parametr <code>T</code> <code>ObjectContext.Translate</code> a <code>ObjectContext.ExecuteStoreQuery</code> metod nemůže být výčet. Tento scénář se teď podporuje.

#### <a name="suggestion"></a>Návrh

Pokud byla metoda přeložit nebo ExecuteStoreQuery volána pro typ výčtu v .NET Framework 4,0, byla vrácena hodnota 0. V případě, že toto chování bylo žádoucí, volání by měla být nahrazena konstantou 0 (nebo ekvivalentem výčtu).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.Translate%60%601(System.Data.Common.DbDataReader,System.String,System.Data.Objects.MergeOption)?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Data.Objects.ObjectContext.ExecuteStoreQuery%60%601(System.String,System.String,System.Data.Objects.MergeOption,System.Object[])?displayProperty=nameWithType></li></ul>|
