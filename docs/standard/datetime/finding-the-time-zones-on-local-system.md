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
ms.openlocfilehash: a65798c46b01bb7a702559d685590ecf7a6f2793
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44262214"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Hledání časových pásem definovaných v lokálním systému

<xref:System.TimeZoneInfo> Třídy nevystavuje veřejný konstruktor. V důsledku toho `new` – klíčové slovo nelze použít k vytvoření nového <xref:System.TimeZoneInfo> objektu. Místo toho <xref:System.TimeZoneInfo> vytváření instance objektů načtěte informace o předdefinovaných časových pásem z registru nebo tak, že vytvoříte vlastní časové pásmo. Toto téma popisuje vytvoření instance časové pásmo z dat uložených v registru. Kromě toho `static` (`shared` v jazyce Visual Basic) vlastnosti <xref:System.TimeZoneInfo> třídy poskytují přístup k místním časovém pásmu koordinovaný univerzální čas (UTC).

> [!NOTE]
> Pro časová pásma, které nejsou definovány v registru, můžete vytvořit vlastní časových pásem voláním přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Vytvoření vlastní časové pásmo je podrobněji popsána [postupy: vytváření časových pásem bez pravidel úpravy](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [postupy: vytváření časových pásem s pravidly úpravy](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) témata. Kromě toho můžete vytvořit instanci <xref:System.TimeZoneInfo> objekt obnovením z serializovaný řetězec s <xref:System.TimeZoneInfo.FromSerializedString%2A> metody. Serializace a deserializace <xref:System.TimeZoneInfo> objekt je popsán v [postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) a [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) témata.

## <a name="accessing-individual-time-zones"></a>Přístup k jednotlivým časových pásem

<xref:System.TimeZoneInfo> Třída poskytuje dva objekty předdefinovaných časové pásmo, které představují čas UTC a místním časovém pásmu. Jsou k dispozici <xref:System.TimeZoneInfo.Utc%2A> a <xref:System.TimeZoneInfo.Local%2A> vlastnosti, v uvedeném pořadí. Pokyny pro přístup k UTC nebo místního času zóny najdete v tématu [postupy: přístup k předdefinované objekty UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md).

Můžete také vytvořit instanci <xref:System.TimeZoneInfo> objekt, který reprezentuje všechny časové pásmo definovaná v registru. Pokyny k vytvoření instance objektu konkrétní časové pásmo, v tématu [postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identifikátory časových pásem

Identifikátor časové pásmo je pole s klíčem, který jednoznačně identifikuje časové pásmo. Většina klíčů jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho. Ve většině případů, jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> vlastnost, která se používá k poskytnutí názvu časového pásma (běžný čas). Existují však výjimky. Vytvoření výčtu časových pásem, který je k dispozici ve vašem systému a Všimněte si jejich přidružené identifikátory je nejlepší způsob, jak Ujistěte se, abyste zadali platný identifikátor.

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](../../../docs/standard/datetime/access-utc-and-local.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Převádění časových údajů mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md)
