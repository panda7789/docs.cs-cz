---
ms.openlocfilehash: 51691ced3f05201f784ccdeffbc130e34748b7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379537"
---
### <a name="wpf-datatemplate-elements-are-now-visible-to-uia"></a>Jsou nyní viditelné pro UIA elementů WPF DataTemplate

|   |   |
|---|---|
|Podrobnosti|Dříve <xref:System.Windows.DataTemplate?displayProperty=name> elementy byly neviditelná pro automatizaci uživatelského rozhraní. Počínaje 4.5, automatizace uživatelského rozhraní se rozpoznat tyto prvky. To je užitečné v mnoha případech ale může dojít k narušení testy, které jsou závislé na stromu UIA neobsahující <xref:System.Windows.DataTemplate?displayProperty=name> elementy.|
|Doporučení|Testy automatizace uživatelského rozhraní pro tuto aplikaci může být nutné aktualizovat, aby se zohlednily stromu UIA nyní včetně dříve neviditelné <xref:System.Windows.DataTemplate?displayProperty=name> elementy. Testy, které očekávají některých prvků bude vedle sebe mohou nyní nutné očekávat dříve neviditelné prvky UIA mezi. Nebo testy, které spoléhají na určité počty nebo indexů pro prvky UIA možná bude nutné aktualizovat s novými hodnotami.|
|Scope|Edge|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Windows.DataTemplate.%23ctor?displayProperty=nameWithType></li><li><xref:System.Windows.DataTemplate.%23ctor(System.Object)?displayProperty=nameWithType></li></ul>|
