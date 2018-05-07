---
title: Ukládání a obnova časových pásem
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET Framework], time zones
- serialization [.NET Framework], time zones
- time zone objects [.NET Framework], restoring
- saving time zones
- time zone objects [.NET Framework], deserializing
- time zones [.NET Framework], saving
- time zones [.NET Framework], restoring
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7c9aefa08d837ce93e718ff32a463d95dabcdc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="saving-and-restoring-time-zones"></a>Ukládání a obnova časových pásem

<xref:System.TimeZoneInfo> Třída vychází z registru pro načtení dat předdefinovaného časového pásma. Dynamická struktura je však registru. Kromě toho informace o časovém pásmu, který obsahuje registru se používá v operačním systému především pro zpracování úpravy času a převody pro aktuálního roku. To má dva hlavní důsledky pro aplikace, které jsou závislé na přesné časové pásmo dat:

* Časové pásmo, které je vyžadována danou aplikací nemusí být definován v registru, nebo bylo přejmenováno nebo odebrat z registru.

* Časové pásmo, která je definována v registru mohou chybět informace o pravidlech konkrétní úprav, které jsou nezbytné pro převody historických časové pásmo.

<xref:System.TimeZoneInfo> Třída řeší tato omezení prostřednictvím své podpory serializace (ukládání) a rekonstrukce (obnovení) dat časového pásma.

## <a name="time-zone-serialization-and-deserialization"></a>Časové pásmo serializace a deserializace

Ukládání a obnovení časového pásma pomocí serializace a deserializace dat časového pásma zahrnuje pouze dvě volání metod:

* Může serializovat <xref:System.TimeZoneInfo> objekt voláním tento objekt <xref:System.TimeZoneInfo.ToSerializedString%2A> metoda. Metoda nepřijímá žádné parametry a vrátí řetězec, který obsahuje informace o časovém pásmu.

* Může deserializovat <xref:System.TimeZoneInfo> z serializovaného řetězce předáním tohoto řetězce pro objekt `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> metoda.

## <a name="serialization-and-deserialization-scenarios"></a>Serializace a deserializace scénáře

Možnost uložení (nebo serializovat) <xref:System.TimeZoneInfo> objekt na řetězec a k obnovení (nebo deserializaci) je pro pozdější použití zvyšuje nástroj a flexibilitu <xref:System.TimeZoneInfo> třídy. Tento oddíl se zabývá některé situace, ve kterých jsou velmi užitečné serializace a deserializace.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializace a deserializace dat časového pásma v aplikaci

Serializované časové pásmo lze obnovit z řetězce, když je to potřeba. Aplikace to třeba udělat, pokud nelze správně převést datum a čas v konkrétní datum rozsahu časovém pásmu z registru načíst. Například data časové pásmo v registru systému Windows XP podporuje jediné pravidlo úprav, zatímco časových pásem definovaných v registru systému Windows Vista obvykle poskytují informace o dvou pravidlech úprav. To znamená, že historické čas převody mohou být nepřesné. Serializace a deserializace dat časového pásma může zpracovávat toto omezení.

V následujícím příkladu, vlastní <xref:System.TimeZoneInfo> třídu, která nemá žádná pravidla úprav není definován pro představují USA Východní standardního časového pásma z 1883 k 1917 před zavedením letního času ve Spojených státech amerických. Vlastní časové pásmo je serializováno v proměnné, která má globální obor. Metodě převodu časového pásma `ConvertUtcTime`, předaný převést časy koordinovaný univerzální čas (UTC). Pokud datum a čas, dojde k 1917 nebo dřívější, vlastní standardní východní časové pásmo je obnoven ze serializovaného řetězce a nahradí časovém pásmu z registru načíst.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Zpracování výjimek časového pásma

Protože registru je dynamická struktura, její obsah se vztahují nechtěným nebo záměrným změnám. To znamená, že časové pásmo, který by měl být definován v registru a, který je vyžadován ke spuštění aplikace nemusí být k dispozici. Bez podpory pro časové pásmo serializace a deserializace, budete mít velmi málo možností ale zpracování výsledné <xref:System.TimeZoneNotFoundException> ukončením aplikace. Však pomocí časové pásmo serializace a deserializace lze zpracovat neočekávanou <xref:System.TimeZoneNotFoundException> obnovením požadováno časového pásma z serializovaného řetězce a aplikace bude dále běžet.

Následující příklad vytvoří a serializuje vlastní centrální standardní časové pásmo. Potom se pokusí načíst centrální standardního časového pásma z registru. Pokud operace načítání vyvolá <xref:System.TimeZoneNotFoundException> nebo <xref:System.InvalidTimeZoneException>, obslužná rutina výjimky deserializuje časové pásmo.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Ukládání serializovaného řetězce a obnovení dat v případě potřeby

V předchozích příkladech mít uložené informace o časovém pásmu na proměnnou string a obnovit jej v případě potřeby. Řetězec, který obsahuje serializovaných čas, informace o zóně může sám sebe být uložený v některém paměťovém médiu, jako je například externí soubor, soubor prostředků však vložený registru nebo aplikace. (Všimněte si, že by měly být uložené informace o vlastních časových pásmech kromě systému časové pásmo klíče v registru.)

Ukládání řetězce serializované časové pásmo tímto způsobem také odděluje rutinu vytváření časového pásma od vlastní aplikace. Například rutina vytvoření časového pásma můžete spustit a vytvořit datový soubor, který obsahuje informace o historických časovém pásmu, který můžete použít aplikaci. Datový soubor může být následně instalován s aplikací a můžete ho otevřít a jeden nebo více jeho časových pásem lze deserializovat, když je aplikace vyžaduje.

Příklad, který používá vložený prostředek k uložení serializovaných dat časového pásma, naleznete v části [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
