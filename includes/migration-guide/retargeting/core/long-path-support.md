---
ms.openlocfilehash: 67e3ff5000ebd38064ed8a57e4fe561afa31f8d8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614477"
---
### <a name="long-path-support"></a>Podpora dlouhých cest

#### <a name="details"></a>Podrobnosti

Počínaje aplikacemi, které cílí na .NET Framework 4.6.2, se podporují dlouhé cesty (z až 32 znaků) a odeberou se omezení 260 znaků (nebo `MAX_PATH` ) na délkách cest. Pro aplikace, které jsou znovu kompilovány pro cílení na .NET Framework 4.6.2, cesty kódu, které dříve vyvolaly, <xref:System.IO.PathTooLongException?displayProperty=fullName> protože cesta překročila 260 znaků, bude nyní vyvolána <xref:System.IO.PathTooLongException?displayProperty=fullName> pouze za následujících podmínek:

- Délka cesty je větší než <xref:System.Int16.MaxValue> (32 767) znaků.
- Operační systém vrátí `COR_E_PATHTOOLONG` nebo jeho ekvivalent.
Pro aplikace, které cílí na .NET Framework 4.6.1 a starší verze, modul runtime automaticky vyvolá <xref:System.IO.PathTooLongException?displayProperty=fullName> vždy, když cesta překračuje 260 znaků.

#### <a name="suggestion"></a>Návrh

U aplikací, které cílí na .NET Framework 4.6.2, se můžete rozhodnout, že podporu dlouhých cest nebudete mít, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />
</runtime>
```

Pro aplikace, které cílí na starší verze .NET Framework, ale běží na .NET Framework 4.6.2 nebo novější, se můžete rozhodnout pro podporu dlouhých cest tím, že do `<runtime>` části souboru přidáte následující `app.config` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />
</runtime>
```

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.6.2       |
| Typ    | Změna cílení |
