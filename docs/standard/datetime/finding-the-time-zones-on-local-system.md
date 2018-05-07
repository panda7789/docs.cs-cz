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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4196ff53a5c26be7c46a8168a30044836af2cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Hledání časových pásem definovaných v lokálním systému

<xref:System.TimeZoneInfo> Třída nevystavuje veřejný konstruktor. V důsledku toho `new` – klíčové slovo nelze použít pro vytvoření nového <xref:System.TimeZoneInfo> objektu. Místo toho <xref:System.TimeZoneInfo> instance objektů načítání informací o předdefinovaných časových pásmech z registru nebo vytváření vlastních časového pásma. Toto téma popisuje, vytváření instancí časového pásma z dat uložených v registru. Kromě toho `static` (`shared` v jazyce Visual Basic) vlastnosti <xref:System.TimeZoneInfo> třída poskytnout přístup k koordinovaný světový čas (UTC) a místním časovém pásmu.

> [!NOTE]
> Časová pásma, které nejsou definovány v registru, můžete vytvořit vlastní časových pásem voláním přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metoda. Vytváření vlastní časové pásmo je popsáno v [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) témata. Kromě toho můžete vytvořit instanci <xref:System.TimeZoneInfo> objekt jeho obnovením ze serializované řetězec s <xref:System.TimeZoneInfo.FromSerializedString%2A> metoda. Serializace a deserializace <xref:System.TimeZoneInfo> objekt je popsán v [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) témata.

## <a name="accessing-individual-time-zones"></a>Přístup k jednotlivých časová pásma

<xref:System.TimeZoneInfo> Třída poskytuje dva objekty předdefinované časové pásmo, které představují čas UTC a místním časovém pásmu. Jsou k dispozici z <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A> vlastnosti, v uvedeném pořadí. Pokyny pro přístup k UTC nebo místního časového pásma naleznete v tématu [postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md).

Můžete také vytvořit instanci <xref:System.TimeZoneInfo> objekt, který reprezentuje všechny časové pásmo definované v registru. Pokyny týkající se vytváření instance objektu konkrétního časového pásma naleznete v tématu [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identifikátory časových pásem

Identifikátor časového pásma je klíčové pole, která jednoznačně identifikuje časové pásmo. Zatímco většina klíče jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho. Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> vlastnosti, která slouží k poskytování název časové pásmo (běžný čas). Existují však výjimky. Vytvoření výčtu časových pásem, který je k dispozici v systému a Všimněte si jejich přidružené identifikátory je nejlepší způsob, jak se ujistěte, že jste zadali platný identifikátor.

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[postupy: přístup k místním ČASEM a předdefinované objekty pásem](../../../docs/standard/datetime/access-utc-and-local.md)
[postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md)
