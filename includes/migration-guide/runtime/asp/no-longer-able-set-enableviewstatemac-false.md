---
ms.openlocfilehash: 78f4d533f1efdc8d43a9ab96508b84a77e3260bc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803242"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Už nebude moct EnableViewStateMac nastavena na hodnotu false

|   |   |
|---|---|
|Podrobnosti|ASP.NET už umožňuje vývojářům zadat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. V zobrazení stavu ověřovací kód zprávy (MAC) je nyní vynucena pro všechny požadavky se stavem vložené zobrazení. Jenom aplikace, které explicitně nastavit vlastnost EnableViewStateMac na <code>false</code> se to týká.|
|Doporučení|EnableViewStateMac musí být předpokládá, že na hodnotu true, a všechny případné chyby MAC musí být vyřešeny (jak je vysvětleno v [tyto pokyny](https://support.microsoft.com/kb/2915218), která obsahuje řešení více rozlišení v závislosti na tom, jaké jsou specifikace co je příčinou chyb MAC).|
|Scope|Hlavní|
|Version|4.5.2|
|type|Modul runtime|

