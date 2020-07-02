---
ms.openlocfilehash: 3f330d5e601d599231ef0336b785e677fe1d114e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616042"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject. GetData teď načítá data jako UTF-8.

#### <a name="details"></a>Podrobnosti

Pro aplikace cílené na .NET Framework 4 nebo spuštěné v .NET Framework 4.5.1 nebo dřívějších verzích `DataObject.GetData` načte data ve formátu HTML jako řetězec ASCII. V důsledku toho jsou znaky, které nejsou ASCII (znaky, jejichž kódy ASCII jsou větší než 0x7F), reprezentovány dvěma náhodnými znaky.<p/>U aplikací, které cílí na .NET Framework 4,5 nebo novější, a jejich spuštění v .NET Framework 4.5.2 `DataObject.GetData` načte data ve formátu HTML jako UTF-8, která představuje znaky větší než 0x7F správně.

#### <a name="suggestion"></a>Návrh

Pokud jste implementovali alternativní řešení potíží s kódováním pomocí řetězců ve formátu HTML (například explicitním kódováním řetězce HTML načteného ze schránky předáním do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=fullName> ) a změnou cílení aplikace z verze 4 na 4,5, mělo by se toto alternativní řešení odebrat. Pokud z nějakého důvodu dojde k původnímu chování, aplikace může cílit na .NET Framework 4,0, aby se toto chování dostalo.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5.2       |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType>
- <xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType>
