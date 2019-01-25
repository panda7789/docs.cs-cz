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
ms.openlocfilehash: 9d783f9e0d098e472dcf67aea394804d6eef2662
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569454"
---
# <a name="saving-and-restoring-time-zones"></a>Ukládání a obnova časových pásem

<xref:System.TimeZoneInfo> Třídy spoléhá na registr a načíst data předdefinované časové pásmo. Registr je však dynamické struktury. Kromě toho informace o časovém pásmu, který obsahuje registru se používá v operačním systému především pro zpracování úpravy času a převody pro aktuálního roku. To má dvě hlavní důsledky pro aplikace, které jsou závislé na datech přesné časové pásmo:

* Časové pásmo, který vyžaduje aplikace nemusí být definováno v registru, nebo byly přejmenovány nebo odebrány z registru.

* Časové pásmo, který je definován v registru mohou chybět informace o pravidlech určité úpravy, které jsou nezbytné pro historické převody.

<xref:System.TimeZoneInfo> Třída adresy prostřednictvím své podpory (uložení) serializace a deserializace (obnovení) časové pásmo dat tato omezení.

## <a name="time-zone-serialization-and-deserialization"></a>Časové pásmo serializace a deserializace

Ukládání a obnova časových pásem serializaci a deserializaci časové pásmo dat zahrnuje dvě volání metody:

* Může serializovat <xref:System.TimeZoneInfo> objekt tohoto objektu voláním <xref:System.TimeZoneInfo.ToSerializedString%2A> metody. Metoda nepřijímá žádné parametry a vrátí řetězec, který obsahuje informace o časovém pásmu.

* Může deserializovat <xref:System.TimeZoneInfo> objekt serializovaný řetězec předáním tohoto řetězce `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> metody.

## <a name="serialization-and-deserialization-scenarios"></a>Serializace a deserializace scénáře

Možnost Uložit (nebo serializovat) <xref:System.TimeZoneInfo> zvyšuje objekt na řetězec a k obnovení (nebo deserializaci) ho pro pozdější použití nástroje a flexibilitu <xref:System.TimeZoneInfo> třídy. Tento oddíl se zabývá některé situace, ve kterých jsou nejužitečnější serializace a deserializace.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializace a deserializace dat časového pásma v aplikaci

Serializovaná časové pásmo je možné obnovit z řetězce, když ho nepotřebují. Aplikace může provést, pokud nelze správně převést datum a čas v rámci určitého období časového pásma z registru načíst. Například časové pásmo data v registru Windows XP podporuje jediné pravidlo úprav, zatímco časových pásem definovaných v registru Windows Vista, obvykle poskytují informace o dvou pravidel úpravy. To znamená, že historické čas převody jsou pravděpodobně nesprávné. Serializace a deserializace dat časového pásma může zpracovávat toto omezení.

V následujícím příkladu, vlastní <xref:System.TimeZoneInfo> představující USA je definována třída, která nemá žádná pravidla úprav Východní oblast (běžný čas) zóny z 1883 k 1917 před zavedením letního času ve Spojených státech. Vlastní časové pásmo je serializován v proměnné, která má globální obor. Metoda převodu časového pásma, `ConvertUtcTime`, je předán převést časy koordinovaný univerzální čas (UTC). Pokud datum a čas, dojde k 1917 nebo starší, vlastní standardní východní časové pásmo je obnoven ze serializovaných řetězec a nahradí časového pásma z registru načíst.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Zpracování výjimek časového pásma

Protože registru je struktura, dynamická, jeho obsah se vztahují náhodného nebo záměrného úpravy. To znamená, že časové pásmo, které musí být definován v registru a, která je vyžadována pro spuštění aplikace nemusí být k dispozici. Bez podpory pro časové pásmo serializace a deserializace, máte malý výběr ale zpracování výsledné <xref:System.TimeZoneNotFoundException> ukončením aplikace. Nicméně pomocí časové pásmo serializace a deserializace můžete zpracovat neočekávanou <xref:System.TimeZoneNotFoundException> obnovením požadované časové pásmo z serializovaný řetězec a aplikace bude pokračovat.

Následující příklad vytvoří a serializuje centrální standardní vlastní časové pásmo. Potom se pokusí načíst centrální standardního časového pásma z registru. Pokud operace načítání vyvolá <xref:System.TimeZoneNotFoundException> nebo <xref:System.InvalidTimeZoneException>, obslužná rutina výjimky deserializuje časové pásmo.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Serializovaný řetězec ukládání a obnovení dat v případě potřeby

V předchozích příkladech máte uložené informace o časovém pásmu k proměnné řetězce a obnovili ji v případě potřeby. Řetězec, který obsahuje serializovaná okamžiku zóny může sám být uložena v některých paměťové médium, například externí soubor soubor prostředků však vloží do registru nebo aplikace. (Všimněte si, že informace o vlastních časová pásma by měla být uložena kromě klíče časové pásmo systému, a v registru.)

Tímto způsobem ukládání řetězec serializované časové pásmo také odděluje rutině vytváření časového pásma od samotná aplikace. Rutině vytváření časového pásma může například provést a vytvoření datového souboru, který obsahuje historická časové pásmo informace, které může aplikace použít. Datový soubor může být potom nainstalovat aplikaci a můžete ho otevřít a nejméně jeden z jeho časových pásem lze deserializovat, když aplikace vyžaduje.

Příklad použití vloženého prostředku k ukládání dat serializovaná časové pásmo, naleznete v tématu [jak: Ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [jak: Obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
