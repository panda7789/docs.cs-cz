---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619936"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Už není možné nastavit EnableViewStateMac na false.

#### <a name="details"></a>Podrobnosti

ASP.NET už neumožňuje vývojářům zadat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code> . Pro všechny požadavky se stavem vloženého zobrazení je nyní vynutil ověřovací kód zprávy o stavu zobrazení (MAC). Ovlivněny jsou pouze aplikace, které explicitně nastavily vlastnost EnableViewStateMac <code>false</code> .

#### <a name="suggestion"></a>Návrh

EnableViewStateMac se musí předpokládat, že má hodnotu true, a všechny výsledné chyby MAC musí být vyřešené (jak je vysvětleno v [těchto pokynech](https://support.microsoft.com/kb/2915218), které obsahují více rozlišení v závislosti na konkrétních hodnotách, které způsobují chyby Mac).

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Hlavní|
|Verze|4.5.2|
|Typ|Modul runtime|
