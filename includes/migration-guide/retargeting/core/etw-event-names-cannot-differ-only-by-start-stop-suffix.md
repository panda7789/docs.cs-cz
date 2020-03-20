---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804455"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Názvy událostí ETW se nemohou lišit pouze příponou "Start" nebo "Stop".

|   |   |
|---|---|
|Podrobnosti|V rozhraní .NET Framework 4.6 a 4.6.1 <xref:System.ArgumentException> modul runtime vyvolá při dvou názvech událostí trasování &quot;&quot; událostí &quot;&quot; pro Windows (ETW) <code>LogUser</code> liší pouze <code>LogUserStart</code>příponou Start nebo Stop (jako když je jedna událost pojmenována a druhá je pojmenována ). V tomto případě runtime nelze vytvořit zdroj události, který nemůže vyzařovat žádné protokolování.|
|Návrh|Chcete-li zabránit výjimce, ujistěte se,&quot; &quot;že&quot; žádné dva názvy událostí se liší pouze příponou &quot;Start nebo Stop. Tento požadavek je odebrán počínaje rozhraním .NET Framework 4.6.2; modul runtime může rozptýlit názvy událostí, &quot;které&quot; &quot;se&quot; liší pouze příponou Start a Stop.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Změna cílení|
