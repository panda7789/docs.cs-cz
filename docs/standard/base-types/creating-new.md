---
title: Vytváření nových řetězců v rozhraní .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103816"
---
# <a name="creating-new-strings-in-net"></a>Vytváření nových řetězců v rozhraní .NET
Rozhraní .NET Framework umožňuje řetězce, které mají být vytvořeny pomocí jednoduché přiřazení a také přetížení konstruktortřídy pro podporu vytváření řetězců pomocí několika různých parametrů. Rozhraní .NET Framework také poskytuje <xref:System.String?displayProperty=nameWithType> několik metod ve třídě, které vytvářejí nové objekty řetězce kombinací několika řetězců, polí řetězců nebo objektů.  
  
## <a name="creating-strings-using-assignment"></a>Vytváření řetězců pomocí přiřazení  
 Nejjednodušší způsob, jak vytvořit <xref:System.String> nový objekt, je jednoduše přiřadit <xref:System.String> literál řetězce k objektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Vytváření řetězců pomocí konstruktoru třídy  
 Přetížení konstruktoru <xref:System.String> třídy můžete použít k vytvoření řetězců z polí znaků. Můžete také vytvořit nový řetězec duplikováním konkrétníznak zadaný počet opakování.  
  
## <a name="methods-that-return-strings"></a>Metody, které vracejí řetězce  
 V následující tabulce je uvedeno několik užitečných metod, které vracejí nové objekty řetězce.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Vytvoří formátovaný řetězec ze sady vstupních objektů.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Vytvoří řetězce ze dvou nebo více řetězců.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Vytvoří nový řetězec kombinací pole řetězců.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Vytvoří nový řetězec vložením řetězce do zadaného indexu existujícího řetězce.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Zkopíruje zadané znaky v řetězci do zadané pozice v poli znaků.|  
  
### <a name="format"></a>Formát  
 Metodu **String.Format** můžete použít k vytvoření formátovaných řetězců a zřetězení řetězců představujících více objektů. Tato metoda automaticky převede všechny předané objekt na řetězec. Například pokud aplikace musí zobrazit hodnotu **Int32** a **DateTime** hodnotu pro uživatele, můžete snadno vytvořit řetězec reprezentovat tyto hodnoty pomocí **Format** metoda. Informace o konvencích formátování použitých touto metodou naleznete v části [o složeném formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 Následující příklad používá metodu **Format** k vytvoření řetězce, který používá celou proměnnou.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 V tomto<xref:System.DateTime.Now%2A?displayProperty=nameWithType> příkladu zobrazí aktuální datum a čas způsobem určeným jazykovou verzí přidruženou k aktuálnímu vláknu.  
  
### <a name="concat"></a>Concat  
 **String.Concat** metoda lze snadno vytvořit nový objekt řetězce ze dvou nebo více existujících objektů. Poskytuje jazykově nezávislý způsob, jak zřetězit řetězce. Tato metoda přijímá všechny třídy, která je odvozena z **System.Object**. Následující příklad vytvoří řetězec ze dvou existujících objektů řetězce a oddělující znak.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Spojit  
 Metoda **String.Join** vytvoří nový řetězec z pole řetězců a oddělovacířetězec. Tato metoda je užitečná, pokud chcete zřetězit více řetězců dohromady, takže seznam možná odděleny čárkou.  
  
 Následující příklad používá mezeru k vytvoření svázání pole řetězců.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Vložit  
 Metoda **String.Insert** vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci. Tato metoda používá index založený na nule. Následující příklad vloží řetězec do páté pozice `MyString` indexu a vytvoří nový řetězec s touto hodnotou.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>Copyto  
 Metoda **String.CopyTo** zkopíruje části řetězce do pole znaků. Můžete zadat počáteční index řetězce i počet znaků, které mají být zkopírovány. Tato metoda přebírá zdrojový index, pole znaků, cílový index a počet znaků ke kopírování. Všechny indexy jsou založeny na nule.  
  
 Následující příklad používá **CopyTo** metoda kopírovat znaky slova "Hello" z objektu řetězce do první pozice indexu pole znaků.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
