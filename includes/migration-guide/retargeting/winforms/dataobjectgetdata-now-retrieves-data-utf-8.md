---
ms.openlocfilehash: e39b4e85b47902babac7a22a93aa64c2f86ef01f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804656"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData nyní načítá data jako UTF-8

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí na rozhraní .NET Framework 4 nebo které běží <code>DataObject.GetData</code> v rozhraní .NET Framework 4.5.1 nebo starších verzích, načte data ve formátu HTML jako řetězec ASCII. V důsledku toho jsou znaky bez ASCII (znaky, jejichž kódy ASCII jsou větší než 0x7F) reprezentovány dvěma náhodnými znaky.<p/>Pro aplikace, které cílí na rozhraní .NET Framework 4.5 nebo novější <code>DataObject.GetData</code> a běží na rozhraní .NET Framework 4.5.2, načte data ve formátu HTML jako UTF-8, který představuje znaky větší než 0x7F správně.|
|Návrh|Pokud jste implementovali řešení problému s kódováním s řetězci ve formátu HTML (například explicitně kódováním řetězce <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>HTML načteného ze schránky předáním ) a znovu cílíte na aplikaci z verze 4 na 4.5, mělo by být toto řešení odebráno. Pokud staré chování je potřeba z nějakého důvodu, aplikace můžete cílit rozhraní .NET Framework 4.0 získat toto chování.|
|Rozsah|Edge|
|Version|4.5.2|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
