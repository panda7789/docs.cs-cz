---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803242"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Již nelze nastavit EnableViewStateMac na false

|   |   |
|---|---|
|Podrobnosti|ASP.NET již umožňuje vývojářům specifikovat <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Ověřovací kód zprávy stavu zobrazení (MAC) je nyní vynucen pro všechny požadavky s vloženým stavem zobrazení. Ovlivněny <code>false</code> jsou pouze aplikace, které explicitně nastavují vlastnost EnableViewStateMac.|
|Návrh|EnableViewStateMac musí být považován za true a všechny výsledné chyby MAC musí být vyřešeny (jak je vysvětleno v [tomto návodu](https://support.microsoft.com/kb/2915218), který obsahuje více rozlišení v závislosti na specifika toho, co je příčinou chyb MAC).|
|Rozsah|Hlavní|
|Version|4.5.2|
|Typ|Modul runtime|
