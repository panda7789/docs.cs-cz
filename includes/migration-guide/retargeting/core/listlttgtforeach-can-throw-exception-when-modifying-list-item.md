---
ms.openlocfilehash: 4e81087431091dfa4d5432d5ea5e2b665be2b130
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62088476"
---
### <a name="listtforeach-can-throw-exception-when-modifying-list-item"></a>Seznam\<T >. ForEach může vyvolat výjimku při úpravě položky seznamu

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5 <xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})> čítač vyvolá výjimku <xref:System.InvalidOperationException?displayProperty=name> výjimku, pokud byl prvek v kolekci volání změněn. Dříve to vyvolání výjimky, by ale může vést ke konfliktům časování.|
|Doporučení|V ideálním případě by kód stanovit nemohou měnit seznamy při vytváření výčtu jejich elementy, protože to je nikdy bezpečný provoz. Chcete-li vrátit k předchozí chování, ale aplikace mohou být zaměřeny na rozhraní .NET Framework 4.0.|
|Rozsah|Edge|
|Version|4.5|
|Type|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.Collections.Generic.List%601.ForEach(System.Action{%600})?displayProperty=nameWithType></li></ul>|
