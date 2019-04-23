---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118471"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Už nebude moct EnableViewStateMac nastavena na hodnotu false

|   |   |
|---|---|
|Podrobnosti|ASP.NET už umožňuje vývojářům zadat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. V zobrazení stavu ověřovací kód zprávy (MAC) je nyní vynucena pro všechny požadavky se stavem vložené zobrazení. Jenom aplikace, které explicitně nastavit vlastnost EnableViewStateMac na <code>false</code> se to týká.|
|Doporučení|EnableViewStateMac musí být předpokládá, že na hodnotu true, a všechny případné chyby MAC musí být vyřešeny (jak je vysvětleno v [tyto pokyny](https://support.microsoft.com/kb/2915218), která obsahuje řešení více rozlišení v závislosti na tom, jaké jsou specifikace co je příčinou chyb MAC).|
|Rozsah|Hlavní|
|Version|4.5.2|
|Type|Modul runtime|
