---
title: Hledání časových pásem definovaných v lokálním systému
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
ms.openlocfilehash: 1e7e3a7a11c1d262f7fcb63e6e12efbe5edf745f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122331"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Hledání časových pásem definovaných v lokálním systému

Třída <xref:System.TimeZoneInfo> nevystavuje veřejný konstruktor. V důsledku toho nelze pomocí klíčového slova `new` vytvořit nový objekt <xref:System.TimeZoneInfo>. Místo toho se instance objektů <xref:System.TimeZoneInfo>, a to načtením informací o předdefinovaných časových pásmech z registru nebo vytvořením vlastního časového pásma. Toto téma popisuje vytvoření instance časového pásma z dat uložených v registru. Kromě toho `static` (`shared` v Visual Basic) vlastnosti třídy <xref:System.TimeZoneInfo> poskytují přístup k koordinovanému univerzálnímu času (UTC) a místnímu časovému pásmu.

> [!NOTE]
> Pro časová pásma, která nejsou definována v registru, můžete vytvořit vlastní časová pásma voláním přetížení metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>. Vytvoření vlastního časového pásma je popsáno v tématu [Postupy: vytváření časových pásem bez pravidel úprav](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [Postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) . Kromě toho můžete vytvořit instanci objektu <xref:System.TimeZoneInfo> tím, že ho obnovíte ze serializovaného řetězce pomocí metody <xref:System.TimeZoneInfo.FromSerializedString%2A>. Serializace a deserializace objektu <xref:System.TimeZoneInfo> je popsána v tématu [Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [Postup: Obnovení časových pásem z témat integrovaných prostředků](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) .

## <a name="accessing-individual-time-zones"></a>Přístup k jednotlivým časovým pásmům

Třída <xref:System.TimeZoneInfo> poskytuje dva předdefinované objekty časového pásma, které představují čas UTC a místní časové pásmo. Jsou dostupné z vlastností <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A>, v uvedeném pořadí. Pokyny k přístupu ke standardu UTC nebo místnímu časovému pásmu naleznete v tématu [How to: Access to a indefinované objekty UTC a místní časové pásmo](../../../docs/standard/datetime/access-utc-and-local.md).

Můžete také vytvořit instanci objektu <xref:System.TimeZoneInfo>, který představuje jakékoli časové pásmo definované v registru. Pokyny k vytvoření instance konkrétního objektu časového pásma naleznete v tématu [How to: instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identifikátory časových pásem

Identifikátor časového pásma je klíčové pole, které jedinečně identifikuje časové pásmo. I když je většina klíčů relativně krátká, identifikátor časového pásma je relativně dlouhý. Ve většině případů jeho hodnota odpovídá vlastnosti <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType>, která slouží k zadání názvu standardního času časového pásma. Existují však výjimky. Nejlepším způsobem, jak zajistit zadání platného identifikátoru, je vytvořit výčet časových pásem dostupných v systému a poznamenat si jejich přidružené identifikátory.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Převádění časů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md)
