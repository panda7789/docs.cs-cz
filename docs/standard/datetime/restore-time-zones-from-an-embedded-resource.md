---
title: 'Postupy: Obnovení časových pásem z integrovaného prostředku'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: cd2119d6d22f3f676b7167ed545aeb058123cfb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122192"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Postupy: Obnovení časových pásem z integrovaného prostředku

Toto téma popisuje, jak obnovit časová pásma uložená v souboru prostředků. Informace a pokyny k ukládání časových pásem najdete v tématu [Postupy: ukládání časových pásem do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Deserializace objektu TimeZoneInfo od vloženého prostředku

1. Pokud časové pásmo, které má být načteno, není vlastním časovým pásmem, zkuste vytvořit instanci pomocí metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>.

2. Vytvořte instanci objektu <xref:System.Resources.ResourceManager> předáním plně kvalifikovaného názvu vloženého souboru prostředku a odkazu na sestavení, které obsahuje soubor prostředků.

   Pokud nemůžete určit plně kvalifikovaný název vloženého souboru prostředků, použijte nástroj [Ildasm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) a prověřte manifest sestavení. Prostředek identifikuje záznam `.mresource`. V tomto příkladu je plně kvalifikovaný název prostředku `SerializeTimeZoneData.SerializedTimeZones`.

   Pokud je soubor prostředků vložen do stejného sestavení, které obsahuje kód pro vytvoření instance časového pásma, můžete získat odkaz na něj voláním metody `static` (`Shared` in Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A>.

3. Pokud volání metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> neproběhne úspěšně nebo pokud je vytvořena instance vlastního časového pásma, načtěte řetězec, který obsahuje serializované časové pásmo voláním metody <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.

4. Deserializace dat časového pásma voláním metody <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="example"></a>Příklad

Následující příklad deserializace objekt <xref:System.TimeZoneInfo> uložený v vloženém souboru prostředků .NET XML.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Tento kód ilustruje zpracování výjimek, aby bylo zajištěno, že je přítomen objekt <xref:System.TimeZoneInfo> vyžadovaný aplikací. Nejprve se pokusí vytvořit instanci objektu <xref:System.TimeZoneInfo> načtením z registru pomocí metody <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>. Pokud časové pásmo nelze vytvořit, kód ho načte z vloženého souboru prostředků.

Vzhledem k tomu, že data pro vlastní časová pásma (časová pásma vytvořená pomocí metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>) nejsou uložena v registru, kód nevolá <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> k vytvoření instance časového pásma pro Palmer, Antarktida. Místo toho se hned vyhledá vložený soubor prostředků, aby se načetl řetězec, který obsahuje data časového pásma před voláním metody <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.

- Následující obory názvů se naimportují:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Ukládání časových pásem do integrovaného prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
