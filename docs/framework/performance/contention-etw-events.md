---
title: Sporné události ETW – .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716138"
---
# <a name="contention-etw-events"></a>Sporné události ETW

Události kolizí jsou vyvolány vždy, když dojde ke sporu pro <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používané modulem runtime. K sporům dochází, když vlákno čeká na zámek, zatímco jiné vlákno má zámek.

Následující tabulka ukazuje klíčové slovo, pod kterým jsou vyvolány události kolizí, a úroveň událostí. Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informační (4)|

Následující tabulka obsahuje informace o události:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Je zahájeno spor. Tato událost nezahrnuje dobu, po kterou vlákno čeká na získání zámku. je vyvolána pouze v případě, že vlákno čeká na získání zámku.|
|`ContentionStop`|91|Spory končí.|

V následující tabulce jsou uvedena data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Příznaky|Win: UInt8|0 pro správu; 1 pro nativní.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR.|

## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
