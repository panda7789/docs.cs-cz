---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664588"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>Objectdisposedexception – vyvolané kontrolu pravopisu WPF

|   |   |
|---|---|
|Podrobnosti|Aplikace WPF někdy dojít k chybě při ukončení aplikace se <xref:System.ObjectDisposedException?displayProperty=name> vyvolané kontrolu pravopisu. Tento problém je vyřešený v rozhraní .NET Framework 4.7 WPF řádně zpracování výjimek a zajistila, že aplikace jsou už nebude mít nepříznivý vliv. Je třeba poznamenat, že by má být dodržen v aplikacích spuštěných v ladicím programu pokračovat občasné výjimkách first-chance.|
|Doporučení|Upgrade na rozhraní .NET Framework 4.7|
|Rozsah|Edge|
|Version|4.6.1|
|Type|Modul runtime|
