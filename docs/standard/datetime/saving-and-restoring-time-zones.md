---
title: Ukládání a obnovování časových pásem
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
ms.openlocfilehash: 8da26988d2e141ac704f0d3756cd8a50602cb3fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281047"
---
# <a name="saving-and-restoring-time-zones"></a>Ukládání a obnovování časových pásem

<xref:System.TimeZoneInfo>Třída spoléhá na to, že registr načte předdefinovaná data časového pásma. Registr je však dynamická struktura. Kromě toho informace o časovém pásmu, které registr obsahuje, používá operační systém primárně k obsluze časových úprav a převodů pro aktuální rok. To má dva zásadní důsledky pro aplikace, které spoléhají na data přesného časového pásma:

- Časové pásmo, které vyžaduje aplikace, nemusí být definováno v registru, nebo mohlo být přejmenováno nebo odebráno z registru.

- Časové pásmo, které je definováno v registru, může chybět informace o konkrétních pravidlech úprav, která jsou nezbytná pro historické převody časových pásem.

<xref:System.TimeZoneInfo>Třída řeší tato omezení prostřednictvím podpory serializace (ukládání) a deserializace (obnovení) dat časového pásma.

## <a name="time-zone-serialization-and-deserialization"></a>Serializace a deserializace časového pásma

Uložení a obnovení časového pásma pomocí serializace a deserializace dat časového pásma zahrnuje pouze dvě volání metod:

- Objekt lze serializovat <xref:System.TimeZoneInfo> voláním <xref:System.TimeZoneInfo.ToSerializedString%2A> metody objektu. Metoda nepřijímá žádné parametry a vrací řetězec, který obsahuje informace o časovém pásmu.

- Můžete deserializovat <xref:System.TimeZoneInfo> objekt ze serializovaného řetězce předáním tohoto řetězce `static` `Shared` metodě (v Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> .

## <a name="serialization-and-deserialization-scenarios"></a>Scénáře serializace a deserializace

Schopnost Uložit (nebo serializovat) <xref:System.TimeZoneInfo> objekt do řetězce a obnovit (nebo deserializovat) pro pozdější použití zvýší jak nástroj, tak i flexibilitu <xref:System.TimeZoneInfo> třídy. Tato část pojednává o některých situacích, ve kterých jsou serializace a deserializace nejužitečnější.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Serializace a deserializace dat časového pásma v aplikaci

Serializované časové pásmo lze obnovit z řetězce, pokud je to potřeba. Aplikace to může udělat, pokud časové pásmo načtené z registru není schopné správně převést datum a čas v rámci určitého rozsahu dat. Například data časového pásma v registru systému Windows XP podporují jedno pravidlo úpravy, zatímco časová pásma definovaná v registru systému Windows Vista obvykle poskytují informace o dvou pravidlech úprav. To znamená, že historické převody času můžou být nepřesné. Toto omezení může zvládnout serializace a deserializace dat časového pásma.

V následujícím příkladu <xref:System.TimeZoneInfo> je vlastní třída, která nemá pravidla úprav, definována tak, aby představovala standardní časové pásmo USA – východ od 1883 do 1917 před začátkem letního času v USA. Vlastní časové pásmo je serializováno v proměnné, která má globální rozsah. Metoda převodu časového pásma, `ConvertUtcTime` , je před převodem předána čas UTC (Coordinated Universal Time). Pokud se datum a čas vyskytnou v 1917 nebo starších verzích, vlastní východní standardní časové pásmo se obnoví ze serializovaného řetězce a nahradí časové pásmo načtené z registru.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Zpracování výjimek časového pásma

Vzhledem k tomu, že registr je dynamická struktura, její obsah podléhá náhodnému nebo úmyslnému provedení úprav. To znamená, že časové pásmo, které by mělo být definováno v registru a které je nutné k úspěšnému provedení aplikace, může chybět. Bez podpory serializace a deserializace časového pásma máte malou volbu, ale chcete-li zpracovat výsledné <xref:System.TimeZoneNotFoundException> ukončení aplikace. Nicméně pomocí serializace a deserializace časového pásma můžete zpracovat neočekávanou <xref:System.TimeZoneNotFoundException> obnovením požadovaného časového pásma ze serializovaného řetězce a aplikace bude nadále běžet.

Následující příklad vytvoří a zaserializace vlastního centrálního časového pásma Standard. Pak se pokusí načíst centrální standardní časové pásmo z registru. Pokud operace načtení vyvolá buď <xref:System.TimeZoneNotFoundException> nebo <xref:System.InvalidTimeZoneException> , obslužná rutina výjimky deserializace časové pásmo.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Uložení serializovaného řetězce a jeho obnovení v případě potřeby

Předchozí příklady obsahují informace o časovém pásmu pro řetězcovou proměnnou a v případě potřeby je obnovila. Řetězec obsahující informace o serializovaném časovém pásmu se ale může ukládat na některé paměťové médium, jako je externí soubor, soubor prostředků vložený do aplikace nebo registr. (Všimněte si, že informace o vlastních časových pásmech by měly být uloženy kromě klíčů časového pásma systému v registru.)

Ukládání serializovaného řetězce časového pásma tímto způsobem také odděluje rutinu vytváření časového pásma přímo z aplikace. Například rutina pro vytvoření časového pásma může spustit a vytvořit datový soubor, který obsahuje historické informace o časovém pásmu, které může aplikace použít. Datový soubor lze následně nainstalovat spolu s aplikací a lze jej otevřít a jeden nebo více jeho časových pásem lze deserializovat, pokud je aplikace vyžaduje.

Příklad, který používá integrovaný prostředek k ukládání serializovaných dat časového pásma, naleznete v tématu [How to: Save a Time Zone to a Embedded](save-time-zones-to-an-embedded-resource.md) a [How to: Restore časová pásma z vloženého prostředku](restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
