---
ms.openlocfilehash: c800b3fcc1eff5d7a669611cb0697aa8c87a37a4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804656"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData nyní načítá data jako UTF-8

|   |   |
|---|---|
|Podrobnosti|Pro aplikace, které cílí na .NET Framework 4 nebo, na kterých běží na rozhraní .NET Framework 4.5.1 nebo starší <code>DataObject.GetData</code> načítá data ve formátu HTML jako řetězec ve formátu ASCII. Ne ASCII znaky (znaky jehož ASCII kódy jsou větší než 0x7F) v důsledku toho jsou reprezentované pomocí dvou náhodných znaků.<p/>Pro aplikace, které cílí .NET Framework 4.5 nebo novější a spustit v rozhraní .NET Framework 4.5.2 <code>DataObject.GetData</code> načítá data ve formátu HTML jako UTF-8, která představuje znaků, které jsou větší než 0x7F správně.|
|Doporučení|Pokud jste implementovali řešení pro kódování problém s řetězce ve formátu HTML (například explicitně kódování HTML řetězec načtení ze schránky ji do <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) a při změně cíle vaší aplikace z verze 4 4.5, který alternativní řešení byste měli odebrat. Pokud z nějakého důvodu je potřeba staré chování, aplikace mohou cílit na .NET Framework 4.0 tohoto chování.|
|Scope|Edge|
|Version|4.5.2|
|type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

