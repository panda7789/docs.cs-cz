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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc3b57659dd6719f72cefba8a6d2f1abe08c0d0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106654"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Postupy: Vytvoření výčtu časových pásem přítomných na počítači

Úspěšná práce s určeným časovým pásmem vyžaduje, aby informace o daném časovém pásmu byly dostupné v systému. Operační systémy Windows XP a Windows Vista tyto informace ukládají do registru. I když celkový počet časových pásem, která existují v celém světě, je velký, registr obsahuje informace o pouze podmnožině. Samotný registr je navíc dynamickou strukturou, jejíž obsah se vztahuje jak na záměrné, tak i na náhodné změny. V důsledku toho aplikace nemůže vždy předpokládat, že konkrétní časové pásmo je definováno a k dispozici v systému. Prvním krokem pro mnoho aplikací, které používají informace o časových pásmech, je určení, zda jsou v místním systému k dispozici požadovaná časová pásma, nebo pokud chcete uživateli poskytnout seznam časových pásem, ze kterých chcete vybrat. To vyžaduje, aby aplikace vyčísluje časová pásma definovaná v místním systému.

> [!NOTE]
> Pokud aplikace spoléhá na přítomnost konkrétního časového pásma, které nemusí být definováno v místním systému, aplikace může zajistit jeho přítomnost serializací a deserializací informací o časovém pásmu. Časové pásmo lze následně přidat do ovládacího prvku seznamu, aby jej uživatel aplikace mohl vybrat. Podrobnosti najdete v tématu [How to: Uložit časová pásma do vloženého](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) prostředku [a postupovat takto: Obnovte časová pásma z vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Vytvoření výčtu časových pásem přítomných v místním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> kolekci objektů. Položky v kolekci jsou seřazené podle jejich <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti. Příklad:

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Zobrazení výčtu jednotlivých <xref:System.TimeZoneInfo> objektů v kolekci `foreach` pomocí smyčky C# `For Each`(in) nebo...`Next` Loop (v Visual Basic) a proveďte jakékoli nezbytné zpracování každého objektu. Například následující kód vytvoří výčet <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> kolekcí objektů vrácených v kroku 1 a zobrazí zobrazovaný název pro každé časové pásmo v konzole.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Prezentace uživatele se seznamem časových pásem přítomných v místním systému

1. Volání <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> metody. Metoda vrátí obecnou <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> <xref:System.TimeZoneInfo> kolekci objektů.

2. Přiřaďte kolekci vrácenou v kroku 1 k `DataSource` vlastnosti ovládacího prvku Windows Forms nebo ASP.NET list.

3. <xref:System.TimeZoneInfo> Načte objekt vybraný uživatelem.

Příklad poskytuje obrázek aplikace pro systém Windows.

## <a name="example"></a>Příklad

V příkladu se spustí aplikace systému Windows, která zobrazuje časová pásma definovaná v systému v seznamu. V příkladu se pak zobrazí dialogové okno, které obsahuje hodnotu <xref:System.TimeZoneInfo.DisplayName%2A> vlastnosti objektu časového pásma vybraného uživatelem.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Většina ovládacích <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> prvků seznam (například ovládací prvek nebo <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> ) umožňuje přiřadit kolekci proměnných objektu ke své `DataSource` <xref:System.Collections.IEnumerable> vlastnosti, pokud kolekce implementuje rozhraní. (Obecná <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> třída to dělá.) Chcete-li zobrazit jednotlivý objekt v kolekci, ovládací prvek volá `ToString` metodu tohoto objektu pro extrakci řetězce, který se používá k reprezentaci objektu. V případě <xref:System.TimeZoneInfo> <xref:System.TimeZoneInfo.DisplayName%2A> objektů `ToString` vrátí<xref:System.TimeZoneInfo> metoda zobrazovaný název objektu (hodnota jeho vlastnosti).

> [!NOTE]
> Vzhledem k tomu, že ovládací prvky `ToString` seznamu volají metodu objektu, můžete přiřadit <xref:System.TimeZoneInfo> kolekci objektů k ovládacímu prvku, nechat ovládací prvek zobrazit smysluplný název pro každý <xref:System.TimeZoneInfo> objekt a načíst objekt, který uživatel vybral. Tím se eliminuje nutnost extrakce řetězce pro každý objekt v kolekci, přiřazení řetězce ke kolekci, která je následně přiřazena `DataSource` vlastnosti ovládacího prvku, načtení řetězce, který uživatel vybral, a pak použití tohoto řetězce k extrakci objektu. který popisuje. 

## <a name="compiling-the-code"></a>Kompilování kódu

Tento příklad vyžaduje:

- Následující obory názvů se naimportují:

  <xref:System>(v C# kódu)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Viz také:

- [Data, časy a časová pásma](../../../docs/standard/datetime/index.md)
- [Postupy: Uložit časová pásma do vloženého prostředku](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Postupy: Obnovení časových pásem z vloženého prostředku](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
