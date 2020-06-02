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
ms.openlocfilehash: d313bbed3cc525a74b90537dd4f1742c09c62cd4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277021"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Hledání časových pásem definovaných v lokálním systému

<xref:System.TimeZoneInfo>Třída nevystavuje veřejný konstruktor. V důsledku toho `new` klíčové slovo nelze použít k vytvoření nového <xref:System.TimeZoneInfo> objektu. Místo toho <xref:System.TimeZoneInfo> jsou vytvořeny instance objektů buď načtením informací o předdefinovaných časových pásmech z registru, nebo vytvořením vlastního časového pásma. Toto téma popisuje vytvoření instance časového pásma z dat uložených v registru. Kromě toho `static` ( `shared` v Visual Basic) vlastnosti <xref:System.TimeZoneInfo> třídy poskytují přístup k koordinovanému univerzálnímu času (UTC) a místnímu časovému pásmu.

> [!NOTE]
> Pro časová pásma, která nejsou definována v registru, můžete vytvořit vlastní časová pásma voláním přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Vytvoření vlastního časového pásma je popsáno v tématu [Postupy: vytváření časových pásem bez pravidel úprav](create-time-zones-without-adjustment-rules.md) a [Postupy: vytváření časových pásem s pravidly úpravy](create-time-zones-with-adjustment-rules.md) . Kromě toho můžete vytvořit instanci <xref:System.TimeZoneInfo> objektu obnovením ze serializovaného řetězce pomocí <xref:System.TimeZoneInfo.FromSerializedString%2A> metody. Serializace a deserializace <xref:System.TimeZoneInfo> objektu je popsána v tématu [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md) a [Postup: Obnovení časových pásem z témat integrovaných prostředků](restore-time-zones-from-an-embedded-resource.md) .

## <a name="accessing-individual-time-zones"></a>Přístup k jednotlivým časovým pásmům

<xref:System.TimeZoneInfo>Třída poskytuje dva předdefinované objekty časového pásma, které představují čas UTC a místní časové pásmo. Jsou k dispozici z <xref:System.TimeZoneInfo.Utc%2A> vlastností a v <xref:System.TimeZoneInfo.Local%2A> uvedeném pořadí. Pokyny k přístupu ke standardu UTC nebo místnímu časovému pásmu naleznete v tématu [How to: Access to a indefinované objekty UTC a místní časové pásmo](access-utc-and-local.md).

Můžete také vytvořit instanci <xref:System.TimeZoneInfo> objektu, který představuje jakékoli časové pásmo definované v registru. Pokyny k vytvoření instance konkrétního objektu časového pásma naleznete v tématu [How to: instance objektu TimeZoneInfo](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Identifikátory časových pásem

Identifikátor časového pásma je klíčové pole, které jedinečně identifikuje časové pásmo. I když je většina klíčů relativně krátká, identifikátor časového pásma je relativně dlouhý. Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> vlastnosti, která slouží k zadání názvu standardního času časového pásma. Existují však výjimky. Nejlepším způsobem, jak zajistit zadání platného identifikátoru, je vytvořit výčet časových pásem dostupných v systému a poznamenat si jejich přidružené identifikátory.

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Postupy: Přístup k předdefinovaným objektům časového pásma UTC a lokálního časového pásma](access-utc-and-local.md)
- [Postupy: Vytvoření instance objektu TimeZoneInfo](instantiate-time-zone-info.md)
- [Převádění časů mezi časovými pásmy](converting-between-time-zones.md)
