---
title: Kolizní události trasování událostí pro Windows – .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857642"
---
# <a name="contention-etw-events"></a>Kolizní události trasování událostí pro Windows

Kolizní události jsou vyvolány pokaždé, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> uzamčení nebo nativní zámky modulem runtime. Kolize nastane, pokud vlákno čeká na zámek a jiné vlákno drží zámek.

V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány události kolize a úroveň události. Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|úroveň|
|-----------------------------------|-----------|
|`ContentionKeyword` (0x4000)|Informativní (4)|

V následující tabulce jsou uvedeny informace o události:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|81|Kolize spustí. Tato událost nezahrnuje množství zprovozňování dobu, než vlákno čeká na získání zámku; je aktivována pouze v případě, že vlákno čeká na získání zámku.|
|`ContentionStop`|91|Kolize skončí.|

V následující tabulce jsou uvedeny data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Příznaky|win:UInt8|0 pro spravované; 1 pro nativní.|
|ClrInstanceID|win:UInt16|Jedinečné ID pro instanci modulu CLR.|

## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
