---
title: Vytváření nových řetězců v .NET
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
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103816"
---
# <a name="creating-new-strings-in-net"></a>Vytváření nových řetězců v .NET
.NET Framework umožňuje vytvoření řetězců pomocí jednoduchého přiřazení a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů. .NET Framework také poskytuje několik metod v <xref:System.String?displayProperty=nameWithType> třídy, které vytvářejí nové řetězcové objekty kombinací několika řetězců, polí řetězců nebo objektů.  
  
## <a name="creating-strings-using-assignment"></a>Vytváření řetězců pomocí přiřazení  
 Nejjednodušší způsob, jak vytvořit nový objekt <xref:System.String>, je jednoduše přiřadit řetězcový literál k objektu <xref:System.String>.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Vytváření řetězců pomocí konstruktoru třídy  
 Pomocí přetížení konstruktoru třídy <xref:System.String> můžete vytvořit řetězce z polí znaků. Můžete také vytvořit nový řetězec duplikováním určitého znaku a zadáním počtu opakování.  
  
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
 Můžete použít metodu **String. Format** pro vytváření formátovaných řetězců a zřetězení řetězců představujících více objektů. Tato metoda automaticky převede všechny předané objekty do řetězce. Například pokud vaše aplikace musí zobrazit hodnotu **Int32** a hodnotu **DateTime** uživateli, můžete snadno vytvořit řetězec, který bude reprezentovat tyto hodnoty pomocí metody **Format** . Informace o konvencích formátování použitých s touto metodou najdete v části [složeného formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 Následující příklad používá metodu **Format** k vytvoření řetězce, který používá proměnnou typu Integer.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 V tomto příkladu<xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem stanoveným jazykovou verzí přidruženou k aktuálnímu vláknu.  
  
### <a name="concat"></a>spojuje  
 Metodu **String. Concat** lze použít k snadnému vytvoření nového objektu řetězce ze dvou nebo více existujících objektů. Poskytuje jazykově nezávislé způsob zřetězení řetězců. Tato metoda přijímá všechny třídy, které jsou odvozeny z typu **System. Object**. Následující příklad vytvoří řetězec ze dvou existujících řetězcových objektů a oddělujícího znaku.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 Metoda **String. Join** vytvoří nový řetězec z pole řetězců a oddělovačového řetězce. Tato metoda je užitečná, pokud chcete zřetězit více řetězců dohromady, takže seznam je pravděpodobně oddělen čárkou.  
  
 Následující příklad používá prostor pro svázání pole řetězců.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 Metoda **String. Insert** vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci. Tato metoda používá index založený na nule. Následující příklad vloží řetězec do páté pozice indexu `MyString` a vytvoří nový řetězec s touto hodnotou.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>Kopírovat  
 Metoda **String. CopyTo** kopíruje části řetězce do pole znaků. Můžete zadat jak počáteční index řetězce, tak počet znaků, které mají být zkopírovány. Tato metoda získá zdrojový index, pole znaků, cílový index a počet znaků, které mají být zkopírovány. Všechny indexy jsou počítány od nuly.  
  
 Následující příklad používá metodu **CopyTo** ke zkopírování znaků slova "Hello" z objektu řetězce na první pozici indexu pole znaků.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
