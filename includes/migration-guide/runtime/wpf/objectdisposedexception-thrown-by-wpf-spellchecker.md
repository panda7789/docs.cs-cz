---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774150"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>Objectdisposedexception – vyvolané kontrolu pravopisu WPF

|   |   |
|---|---|
|Podrobnosti|Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu. Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv. Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Modul runtime|
