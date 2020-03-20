---
ms.openlocfilehash: a3f5f512fd17ab2b076f868be24e5c73d8698c49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802535"
---
### <a name="objectdisposedexception-thrown-by-wpf-spellchecker"></a>ObjectDisposedException vyvolána WPF kontrola pravopisu

|   |   |
|---|---|
|Podrobnosti|WPF aplikace občas selhání během <xref:System.ObjectDisposedException?displayProperty=name> vypnutí aplikace s vyvolána kontrola pravopisu. To je opraveno v rozhraní .NET Framework 4.7 WPF zpracováním výjimky řádně a tím zajistit, že aplikace již nejsou nepříznivě ovlivněny. Je třeba poznamenat, že příležitostné výjimky první šance by i nadále být pozorovány v aplikacích spuštěných v ladicím programu.|
|Návrh|Upgrade na rozhraní .NET Framework 4.7|
|Rozsah|Edge|
|Version|4.6.1|
|Typ|Modul runtime|
