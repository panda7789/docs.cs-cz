---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614453"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Názvy událostí ETW se nemůžou lišit jenom od přípony "Start" nebo "Stop".

#### <a name="details"></a>Podrobnosti

V .NET Framework 4,6 a 4.6.1 modul runtime vyvolá výjimku, <xref:System.ArgumentException> Pokud se dva názvy událostí trasování událostí pro Windows (ETW) liší pouze příponou "Start" nebo "Stop" (jako když jedna událost je pojmenována `LogUser` a jiná má název `LogUserStart` ). V takovém případě modul runtime nemůže vytvořit zdroj události, který nemůže vygenerovat žádné protokolování.

#### <a name="suggestion"></a>Návrh

Chcete-li zabránit výjimce, zajistěte, aby se žádné dva názvy událostí nelišily pouze příponou "Start" nebo "Stop". Tento požadavek se odebere počínaje .NET Framework 4.6.2; modul runtime může lišit názvy událostí, které se liší pouze příponou "Start" a "Stop".

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.6         |
| Typ    | Změna cílení |
