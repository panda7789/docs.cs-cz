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
ms.openlocfilehash: b1cece13c88b3a49c9c4c90045a07dd009d4282d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281320"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Postupy: Obnovení časových pásem z integrovaného prostředku

Toto téma popisuje, jak obnovit časová pásma uložená v souboru prostředků. Informace a pokyny k ukládání časových pásem najdete v tématu [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Deserializace objektu TimeZoneInfo od vloženého prostředku

1. Pokud časové pásmo, které má být načteno, není vlastním časovým pásmem, zkuste vytvořit instanci pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody.

2. Vytvořte instanci <xref:System.Resources.ResourceManager> objektu předáním plně kvalifikovaného názvu vloženého souboru prostředků a odkazu na sestavení, které obsahuje soubor prostředků.

   Pokud nemůžete určit plně kvalifikovaný název vloženého souboru prostředků, použijte nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) a prověřte manifest sestavení. `.mresource`Položka identifikuje prostředek. V tomto příkladu je plně kvalifikovaný název prostředku `SerializeTimeZoneData.SerializedTimeZones` .

   Pokud je soubor prostředků vložen do stejného sestavení, které obsahuje kód pro vytvoření instance časového pásma, můžete na něj získat odkaz voláním `static` `Shared` metody (v Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .

3. Pokud volání <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody dojde k chybě nebo pokud je vytvořena instance vlastního časového pásma, načtěte řetězec, který obsahuje serializované časové pásmo voláním <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> metody.

4. Deserializace dat časového pásma voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="example"></a>Příklad

Následující příklad deserializace <xref:System.TimeZoneInfo> objekt uložený v vloženém souboru prostředků .NET XML.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Tento kód ilustruje zpracování výjimek, aby bylo zajištěno, že <xref:System.TimeZoneInfo> objekt vyžadovaný aplikací je přítomen. Nejprve se pokusí vytvořit instanci <xref:System.TimeZoneInfo> objektu jejich načtením z registru pomocí <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> metody. Pokud časové pásmo nelze vytvořit, kód ho načte z vloženého souboru prostředků.

Vzhledem k tomu, že data pro vlastní časová pásma (časová pásma vytvořená pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody) nejsou uložena v registru, kód nevolá <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pro vytvoření instance časového pásma pro Palmer, Antarktida. Místo toho se hned vyhledá vložený soubor prostředků, aby se načetl řetězec, který obsahuje data časového pásma před voláním <xref:System.TimeZoneInfo.FromSerializedString%2A> metody.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.

- Následující obory názvů se naimportují:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Přehled časových pásem](time-zone-overview.md)
- [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md)
