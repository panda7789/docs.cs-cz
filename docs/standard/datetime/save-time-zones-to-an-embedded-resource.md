---
title: 'Postupy: Ukládání časových pásem do integrovaného prostředku'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107161"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Postupy: Ukládání časových pásem do integrovaného prostředku

Aplikace pracující s časovým pásmem často vyžaduje přítomnost konkrétního časového pásma. Vzhledem k tomu, že dostupnost jednotlivých <xref:System.TimeZoneInfo> objektů závisí na informacích uložených v registru místního systému, nemusí být k dispozici ani běžně dostupná časová pásma. Kromě toho informace o vlastních časových pásmech, které jsou vytvořeny pomocí <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody, nejsou uloženy spolu s dalšími informacemi o časovém pásmu v registru. Chcete-li zajistit, aby tato časová pásma byla k dispozici v případě potřeby, můžete je uložit jejich serializací a později je obnovit jejich deserializací.

K serializaci <xref:System.TimeZoneInfo> objektu obvykle dochází z aplikace pracující s časovým pásmem. V závislosti na úložišti dat, které se používá pro <xref:System.TimeZoneInfo> blokování serializovaných objektů, může být data časového pásma serializována jako součást Instalační rutiny nebo Instalační rutiny (například když jsou data uložena v klíči aplikace registru) nebo jako součást rutiny, která spouští nástroj. před kompilací konečné aplikace (například když jsou serializovaná data uložena v souboru prostředků .NET XML (. resx)).

Kromě souboru prostředků, který je zkompilován s aplikací, lze použít několik dalších úložišť dat pro informace o časovém pásmu. Patří mezi ně například:

- Registr. Všimněte si, že aplikace by měla použít podklíče vlastního klíče aplikace k uložení dat vlastního časového pásma namísto použití podklíčů zón HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time.

- Konfigurační soubory.

- Jiné systémové soubory.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Uložení časového pásma pomocí serializace do souboru. resx

1. Načtěte existující časové pásmo nebo vytvořte nové časové pásmo.

   Chcete-li načíst existující časové pásmo, [Přečtěte si téma How to: Přístup k předdefinovaným objektům](../../../docs/standard/datetime/access-utc-and-local.md) UTC a místnímu časovému pásmu a [postupy: Vytvoří instanci objektu](../../../docs/standard/datetime/instantiate-time-zone-info.md)TimeZoneInfo.

   Chcete-li vytvořit nové časové pásmo, zavolejte jedno z přetížení <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> metody. Další informace najdete v tématu [jak: Vytváření časových pásem bez pravidel](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) úprav a [postupy: Vytváření časových pásem s pravidly](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)úpravy

2. <xref:System.TimeZoneInfo.ToSerializedString%2A> Zavolejte metodu pro vytvoření řetězce, který obsahuje data časového pásma.

3. Vytvořte instanci <xref:System.IO.StreamWriter> objektu zadáním názvu a volitelně cesty k souboru. resx konstruktoru třídy. <xref:System.IO.StreamWriter>

4. Vytvořte instanci <xref:System.IO.StreamWriter> <xref:System.Resources.ResXResourceWriter> objektu předáním objektu konstruktoru třídy. <xref:System.Resources.ResXResourceWriter>

5. Předat serializovanému řetězci časového pásma do <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> metody.

6. Volání <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> metody.

7. Volání <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> metody.

8. Zavřete objekt voláním jeho <xref:System.IO.StreamWriter.Close%2A>metody. <xref:System.IO.StreamWriter>

9. Přidejte vygenerovaný soubor. resx do projektu aplikace Visual Studio aplikace.

10. V okně **vlastnosti** v sadě Visual Studio se ujistěte, že vlastnost **Akce sestavení** souboru. resx je nastavená na **Integrovaný prostředek**.

## <a name="example"></a>Příklad

Následující příklad serializace <xref:System.TimeZoneInfo> objektu, který představuje centrální standardní čas <xref:System.TimeZoneInfo> a objekt, který představuje stanici Palmer, Antarktida čas souboru prostředků .NET XML s názvem SerializedTimeZones. resx. Střední běžný čas je obvykle definován v registru; Palmer stanice je Antarktida vlastním časovým pásmem.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Tento příklad serializace <xref:System.TimeZoneInfo> objekty tak, aby byly k dispozici v souboru prostředků v době kompilace.

Vzhledem k tomu, že Metodapřidádosouboruprostředků.NETXMLúplnéinformaceohlavičce,nelzejipoužítkpřidáníprostředkůdoexistujícíhosouboru.<xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> Tento příklad zpracovává tuto kontrolu pomocí kontroly souboru SerializedTimeZones. resx a pokud existuje, ukládá všechny jeho prostředky jiné než dvě serializovaná časová pásma do obecného <xref:System.Collections.Generic.Dictionary%602> objektu. Existující soubor se pak odstraní a stávající prostředky se přidají do nového souboru SerializedTimeZones. resx. Do tohoto souboru jsou přidána také Serializovaná data časového pásma.

Pole klíče (nebo **Name**) prostředků nesmí obsahovat vložené mezery. <xref:System.String.Replace%28System.String%2CSystem.String%29> Metoda je volána pro odebrání všech vložených mezer v identifikátorech časového pásma předtím, než jsou přiřazeny k souboru prostředků.

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Do projektu se přidá odkaz na System. Windows. Forms. dll a System. Core. dll.

- Následující obory názvů se naimportují:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Přehled časových pásem](../../../docs/standard/datetime/time-zone-overview.md)
- [Postupy: Obnovení časových pásem z vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
