---
title: Vytváření nových řetězců v .NET
description: Naučte se vytvářet řetězce pomocí přiřazení, konstruktorů tříd nebo metod System. String, které spojují několik řetězců, polí řetězců nebo objektů v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: b44d0f8e1717ead72e28f0be644644961d1482b6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596445"
---
# <a name="creating-new-strings-in-net"></a>Vytváření nových řetězců v .NET
.NET Framework umožňuje vytvoření řetězců pomocí jednoduchého přiřazení a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů. .NET Framework také poskytuje několik metod ve <xref:System.String?displayProperty=nameWithType> třídě, které vytvářejí nové řetězcové objekty kombinací několika řetězců, polí řetězců nebo objektů.  
  
## <a name="creating-strings-using-assignment"></a>Vytváření řetězců pomocí přiřazení  
 Nejjednodušší způsob, jak vytvořit nový <xref:System.String> objekt, je jednoduše přiřadit řetězcový literál <xref:System.String> objektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Vytváření řetězců pomocí konstruktoru třídy  
 Pomocí přetížení <xref:System.String> konstruktoru třídy lze vytvořit řetězce z polí znaků. Můžete také vytvořit nový řetězec duplikováním určitého znaku a zadáním počtu opakování.  
  
## <a name="methods-that-return-strings"></a>Metody, které vracejí řetězce  
 Následující tabulka uvádí několik užitečných metod, které vracejí nové řetězcové objekty.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Vytvoří formátovaný řetězec ze sady vstupních objektů.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Vytvoří řetězce ze dvou nebo více řetězců.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Vytvoří nový řetězec kombinováním pole řetězců.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Vytvoří nový řetězec vložením řetězce do zadaného indexu stávajícího řetězce.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Zkopíruje zadané znaky v řetězci do zadané pozice v poli znaků.|  
  
### <a name="format"></a>Formát  
 Můžete použít metodu **String. Format** pro vytváření formátovaných řetězců a zřetězení řetězců představujících více objektů. Tato metoda automaticky převede všechny předané objekty do řetězce. Například pokud vaše aplikace musí zobrazit hodnotu **Int32** a hodnotu **DateTime** uživateli, můžete snadno vytvořit řetězec, který bude reprezentovat tyto hodnoty pomocí metody **Format** . Informace o konvencích formátování použitých s touto metodou najdete v části [složeného formátování](composite-formatting.md).  
  
 Následující příklad používá metodu **Format** k vytvoření řetězce, který používá proměnnou typu Integer.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 V tomto příkladu <xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určeným jazykovou verzí přidruženou k aktuálnímu vláknu.  
  
### <a name="concat"></a>Concat  
 Metodu **String. Concat** lze použít k snadnému vytvoření nového objektu řetězce ze dvou nebo více existujících objektů. Poskytuje jazykově nezávislé způsob zřetězení řetězců. Tato metoda přijímá všechny třídy, které jsou odvozeny z typu **System. Object**. Následující příklad vytvoří řetězec ze dvou existujících řetězcových objektů a oddělujícího znaku.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Spojit  
 Metoda **String. Join** vytvoří nový řetězec z pole řetězců a oddělovačového řetězce. Tato metoda je užitečná, pokud chcete zřetězit více řetězců dohromady, takže seznam je pravděpodobně oddělen čárkou.  
  
 Následující příklad používá prostor pro svázání pole řetězců.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Vložit  
 Metoda **String. Insert** vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci. Tato metoda používá index založený na nule. Následující příklad vloží řetězec do páté pozice indexu v `MyString` a vytvoří nový řetězec s touto hodnotou.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>Kopírovat  
 Metoda **String. CopyTo** kopíruje části řetězce do pole znaků. Můžete zadat jak počáteční index řetězce, tak počet znaků, které mají být zkopírovány. Tato metoda získá zdrojový index, pole znaků, cílový index a počet znaků, které mají být zkopírovány. Všechny indexy jsou počítány od nuly.  
  
 Následující příklad používá metodu **CopyTo** ke zkopírování znaků slova "Hello" z objektu řetězce na první pozici indexu pole znaků.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](basic-string-operations.md)
- [Složené formátování](composite-formatting.md)
