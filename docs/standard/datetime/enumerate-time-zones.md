---
title: 'Postupy: Vytvoření výčtu časových pásem přítomných na počítači'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 8f1cc9d58bc0f169d458854eac6568caaa4481c7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286129"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Postupy: Vytvoření výčtu časových pásem přítomných na počítači

Úspěšná práce s určeným časovým pásmem vyžaduje, aby informace o daném časovém pásmu byly dostupné v systému. Operační systémy Windows XP a Windows Vista tyto informace ukládají do registru. I když celkový počet časových pásem, která existují v celém světě, je velký, registr obsahuje informace o pouze podmnožině. Samotný registr je navíc dynamickou strukturou, jejíž obsah se vztahuje jak na záměrné, tak i na náhodné změny. V důsledku toho aplikace nemůže vždy předpokládat, že konkrétní časové pásmo je definováno a k dispozici v systému. Prvním krokem pro mnoho aplikací, které používají informace o časových pásmech, je určení, zda jsou v místním systému k dispozici požadovaná časová pásma, nebo pokud chcete uživateli poskytnout seznam časových pásem, ze kterých chcete vybrat. To vyžaduje, aby aplikace vyčísluje časová pásma definovaná v místním systému.

> [!NOTE]
> Pokud aplikace spoléhá na přítomnost konkrétního časového pásma, které nemusí být definováno v místním systému, aplikace může zajistit jeho přítomnost serializací a deserializací informací o časovém pásmu. Časové pásmo lze následně přidat do ovládacího prvku seznamu, aby jej uživatel aplikace mohl vybrat. Podrobnosti najdete v tématu [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md) a [Postup: Obnovení časových pásem z vloženého prostředku](restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Vytvoření výčtu časových pásem přítomných v místním systému

1. Zavolejte <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metodu. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekci <xref:System.TimeZoneInfo> objektů. Položky v kolekci jsou seřazené podle jejich <xref:System.TimeZoneInfo.DisplayName%2A> Vlastnosti. Například:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Zobrazení výčtu jednotlivých <xref:System.TimeZoneInfo> objektů v kolekci pomocí `foreach` smyčky (v jazyce C#) nebo `For Each` ...`Next` Loop (v Visual Basic) a proveďte jakékoli nezbytné zpracování každého objektu. Například následující kód vytvoří výčet <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekcí <xref:System.TimeZoneInfo> objektů vrácených v kroku 1 a zobrazí zobrazovaný název pro každé časové pásmo v konzole.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Prezentace uživatele se seznamem časových pásem přítomných v místním systému

1. Zavolejte <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metodu. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> kolekci <xref:System.TimeZoneInfo> objektů.

2. Přiřaďte kolekci vrácenou v kroku 1 k `DataSource` vlastnosti ovládacího prvku Windows Forms nebo ASP.NET list.

3. Načte <xref:System.TimeZoneInfo> objekt vybraný uživatelem.

Příklad poskytuje obrázek aplikace pro systém Windows.

## <a name="example"></a>Příklad

V příkladu se spustí aplikace systému Windows, která zobrazuje časová pásma definovaná v systému v seznamu. V příkladu se pak zobrazí dialogové okno, které obsahuje hodnotu <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti objektu časového pásma vybraného uživatelem.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Většina ovládacích prvků seznam (například <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> ovládací prvek nebo) umožňuje přiřadit kolekci proměnných objektu ke své `DataSource` vlastnosti, pokud kolekce implementuje <xref:System.Collections.IEnumerable> rozhraní. (Obecná <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> Třída to dělá.) Chcete-li zobrazit jednotlivý objekt v kolekci, ovládací prvek volá metodu tohoto objektu `ToString` pro extrakci řetězce, který se používá k reprezentaci objektu. V případě <xref:System.TimeZoneInfo> objektů `ToString` vrátí metoda <xref:System.TimeZoneInfo> Zobrazovaný název objektu (hodnota jeho <xref:System.TimeZoneInfo.DisplayName%2A> Vlastnosti).

> [!NOTE]
> Vzhledem k tomu, že ovládací prvky seznamu volají `ToString` metodu objektu, můžete přiřadit kolekci <xref:System.TimeZoneInfo> objektů k ovládacímu prvku, nechat ovládací prvek zobrazit smysluplný název pro každý objekt a načíst <xref:System.TimeZoneInfo> objekt, který uživatel vybral. Tím se eliminuje nutnost extrakce řetězce pro každý objekt v kolekci, přiřazení řetězce ke kolekci, která je následně přiřazena vlastnosti ovládacího prvku `DataSource` , načtení řetězce, který uživatel vybral, a pak pomocí tohoto řetězce k extrakci objektu, který popisuje.

## <a name="compiling-the-code"></a>Zkompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  <xref:System>(v kódu jazyka C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Viz také

- [Data, časy a časová pásma](index.md)
- [Postupy: ukládání časových pásem do vloženého prostředku](save-time-zones-to-an-embedded-resource.md)
- [Postupy: Obnovení časových pásem z integrovaného prostředku](restore-time-zones-from-an-embedded-resource.md)
