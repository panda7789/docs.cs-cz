---
title: 'Postupy: vytvoření instance objektu TimeZoneInfo'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e15e7f8968d7edf87ae3cd709d8fb26a2f49826a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572044"
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a>Postupy: vytvoření instance objektu TimeZoneInfo

Nejběžnější způsob vytvoření instance objektu <xref:System.TimeZoneInfo> objekt je k načtení informací o jej z registru. Toto téma popisuje, jak vytvořit instanci <xref:System.TimeZoneInfo> objekt z registru místního systému.

### <a name="to-instantiate-a-timezoneinfo-object"></a>K vytvoření instance objektu TimeZoneInfo

1. Deklarace <xref:System.TimeZoneInfo> objektu.

2. Volání `static` (`Shared` v jazyce Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> metoda.

3. Zpracujte jakékoli výjimky vyvolané metodou, zejména v <xref:System.TimeZoneNotFoundException> , je vyvolána, pokud se časové pásmo není definován v registru.

## <a name="example"></a>Příklad

Následující kód načte <xref:System.TimeZoneInfo> objekt, který představuje standardní východní časové pásmo a zobrazí východní běžný čas, který odpovídá na místní čas.

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> Jediný parametr metody je identifikátor časové pásmo, které chcete zjistit, který odpovídá objektu <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> vlastnost. Identifikátor časového pásma je klíčové pole, která jednoznačně identifikuje časové pásmo. Zatímco většina klíče jsou poměrně krátké, identifikátor časové pásmo je poměrně dlouho. Ve většině případů jeho hodnota odpovídá <xref:System.TimeZoneInfo.StandardName%2A> vlastnost <xref:System.TimeZoneInfo> objekt, který slouží k poskytování název časové pásmo (běžný čas). Existují však výjimky. Vytvoření výčtu časových pásem, který je k dispozici v systému a Všimněte si identifikátory časových pásem v nich je nejlepší způsob, jak se ujistěte, že jste zadali platný identifikátor. Pro ilustraci, najdete v části [postupy: vytvoření výčtu časových pásem přítomných na počítači](../../../docs/standard/datetime/enumerate-time-zones.md). [Hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) téma také obsahuje seznam identifikátorů vybranému časovému pásmu.

Pokud se časové pásmo nalezeno, vrátí metoda jeho <xref:System.TimeZoneInfo> objektu. Pokud není nalezen časové pásmo, vyvolá metoda <xref:System.TimeZoneNotFoundException>. Pokud je nalezena časové pásmo, ale jeho data jsou poškozená nebo nekompletní, vyvolá metoda <xref:System.InvalidTimeZoneException>.

Pokud vaše aplikace závisí na časové pásmo, které musí být k dispozici, měli byste nejprve zavolat <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> a načíst informace o časovém pásmu z registru. Pokud selže volání metody vaší obslužné rutiny výjimky by pak buď vytvořit novou instanci třídy časové pásmo nebo jej znovu vytvořit pomocí deserializace serializovaného <xref:System.TimeZoneInfo> objektu. V tématu [postupy: obnovení časových pásem ze vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) příklad.

## <a name="see-also"></a>Viz také

[Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
[hledání časových pásem definovaných v lokálním systému](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[postupy: přístup k místním ČASEM a předdefinované objekty zóny](../../../docs/standard/datetime/access-utc-and-local.md)
