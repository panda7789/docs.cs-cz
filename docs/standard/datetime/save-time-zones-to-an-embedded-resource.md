---
title: 'Postupy: ukládání časových pásem do vloženého prostředku'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
ms.openlocfilehash: aaee4e82d09e8b604d06dadb5a5eefe8d2e1f307
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123775"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Postupy: ukládání časových pásem do vloženého prostředku

Aplikace pracující s časovým pásmem často vyžaduje přítomnost konkrétního časového pásma. Vzhledem k tomu, že dostupnost jednotlivých <xref:System.TimeZoneInfo> objektů závisí na informacích uložených v registru místního systému, nemusí být k dispozici ani běžně dostupná časová pásma. Navíc informace o vlastních časových pásmech, které jsou vytvořeny pomocí metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>, nejsou uloženy v registru s dalšími informacemi o časovém pásmu. Chcete-li zajistit, aby tato časová pásma byla k dispozici v případě potřeby, můžete je uložit jejich serializací a později je obnovit jejich deserializací.

K serializaci objektu <xref:System.TimeZoneInfo> dochází obvykle od aplikace pracující s časovým pásmem. V závislosti na úložišti dat použitého pro blokování serializovaných <xref:System.TimeZoneInfo> objektů mohou být data časového pásma serializována jako součást rutiny instalace nebo instalace (například když jsou data uložena v klíči aplikace registru) nebo jako součást rutiny nástroje, která se spouští před Konečná aplikace je zkompilována (například když jsou serializovaná data uložena v souboru prostředků .NET XML (. resx)).

Kromě souboru prostředků, který je zkompilován s aplikací, lze použít několik dalších úložišť dat pro informace o časovém pásmu. Patří mezi ně například:

- Registr. Všimněte si, že aplikace by měla použít podklíče vlastního klíče aplikace k uložení dat vlastního časového pásma namísto použití podklíčů zón HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time.

- Konfigurační soubory.

- Jiné systémové soubory.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Uložení časového pásma pomocí serializace do souboru. resx

1. Načtěte existující časové pásmo nebo vytvořte nové časové pásmo.

   Chcete-li načíst existující časové pásmo, přečtěte si téma [Postup: přístup k předdefinovaným objektům UTC a místnímu časovému pásmu](../../../docs/standard/datetime/access-utc-and-local.md) a [Postupy: vytvoření instance objektu TimeZoneInfo](../../../docs/standard/datetime/instantiate-time-zone-info.md).

   Chcete-li vytvořit nové časové pásmo, zavolejte jedno z přetížení metody <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>. Další informace najdete v tématu [Postupy: vytváření časových pásem bez pravidel úprav](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) a [Postupy: vytváření časových pásem s pravidly úprav](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).

2. Voláním metody <xref:System.TimeZoneInfo.ToSerializedString%2A> vytvoříte řetězec, který obsahuje data časového pásma.

3. Vytvořte instanci objektu <xref:System.IO.StreamWriter> tím, že zadáte název a případně cestu k souboru. resx konstruktoru třídy <xref:System.IO.StreamWriter>.

4. Vytvořte instanci objektu <xref:System.Resources.ResXResourceWriter> předáním objektu <xref:System.IO.StreamWriter> do konstruktoru třídy <xref:System.Resources.ResXResourceWriter>.

5. Předejte serializovaný řetězec časového pásma do metody <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType>.

6. Zavolejte metodu <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.

7. Zavolejte metodu <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.

8. Zavřete objekt <xref:System.IO.StreamWriter> voláním jeho metody <xref:System.IO.StreamWriter.Close%2A>.

9. Přidejte vygenerovaný soubor. resx do projektu aplikace Visual Studio aplikace.

10. V okně **vlastnosti** v sadě Visual Studio se ujistěte, že vlastnost **Akce sestavení** souboru. resx je nastavená na **Integrovaný prostředek**.

## <a name="example"></a>Příklad

Následující příklad serializace <xref:System.TimeZoneInfo> objekt, který představuje střední čas a <xref:System.TimeZoneInfo> objekt, který představuje stanici Palmer, Antarktida čas souboru prostředků .NET XML s názvem SerializedTimeZones. resx. Střední běžný čas je obvykle definován v registru; Palmer stanice je Antarktida vlastním časovým pásmem.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Tento příklad serializace <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.

Vzhledem k tomu, že metoda <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> přidá do souboru prostředků .NET XML úplné informace o hlavičce, nelze ji použít k přidání prostředků do existujícího souboru. Tento příklad zpracovává tuto kontrolu pomocí kontroly souboru SerializedTimeZones. resx a pokud existuje, ukládá všechny jeho prostředky kromě dvou serializovaných časových pásem do obecného <xref:System.Collections.Generic.Dictionary%602> objektu. Existující soubor se pak odstraní a stávající prostředky se přidají do nového souboru SerializedTimeZones. resx. Do tohoto souboru jsou přidána také Serializovaná data časového pásma.

Pole klíče (nebo **Name**) prostředků nesmí obsahovat vložené mezery. Je volána metoda <xref:System.String.Replace%28System.String%2CSystem.String%29> pro odebrání všech vložených mezer v identifikátorech časového pásma předtím, než jsou přiřazeny k souboru prostředků.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.

- Následující obory názvů se naimportují:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Obnovení časových pásem z integrovaného prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
