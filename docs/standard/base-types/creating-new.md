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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9f0c487d3d04af998fb1c3339d736e9bb043374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="creating-new-strings-in-net"></a>Vytváření nových řetězců v .NET
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umožňuje vytvoření jednoduché přiřazení řetězců a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také poskytuje několik metod <xref:System.String?displayProperty=nameWithType> třídu, která vytvořit nový řetězec sloučením několika řetězců, pole řetězců, objekty nebo objekty.  
  
## <a name="creating-strings-using-assignment"></a>Vytváření řetězců pomocí přiřazení  
 Nejjednodušší způsob, jak vytvořit nový <xref:System.String> objekt je jednoduše přiřadit řetězcový literál <xref:System.String> objektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Vytváření řetězců pomocí konstruktoru třídy  
 Můžete použít přetížení metody <xref:System.String> třída – konstruktor k vytvoření řetězce z pole znaků. Nový řetězec také vytvoříte duplikování určitého znaku zadaného počtu opakování.  
  
## <a name="methods-that-return-strings"></a>Metody, které vracejí řetězce  
 Následující tabulka uvádí několik užitečných metod, které vracejí nové objekty řetězec.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Vytvoří formátovaný řetězec ze sady vstupní objektů.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Vytvoří řetězce ze dvou nebo více řetězců.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Vytvoří nový řetězec kombinováním pole řetězců.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Vytvoří nový řetězec vložením řetězce zadaný index existující řetězec.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Kopíruje zadané znaky v řetězci na zadané pozici v pole znaků.|  
  
### <a name="format"></a>Formát  
 Můžete použít **String.Format** metoda pro vytvoření formátované řetězce a zřetězení řetězců představující více objektů. Tato metoda automaticky převede jakýkoli předaný objekt na řetězec. Například, pokud aplikace vyžaduje zobrazení **Int32** hodnotu a **data a času** hodnotu pro uživatele, můžete snadno vytvořit řetězec představující tyto hodnoty pomocí **formátu**metoda. Informace o konvencích formátování použitého tuto metodu, najdete v části na [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 Následující příklad používá **formát** metodu pro vytvoření řetězec, který používá proměnnou celé číslo.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 V tomto příkladu<xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určeného jazykovou verzi spojenou s aktuálním vláknem.  
  
### <a name="concat"></a>concat  
 **String.Concat** metoda lze snadno vytvořit nový objekt řetězec ze dvou nebo více existujících objektů. Poskytuje způsob nezávislé na jazyku ke zřetězení řetězců. Tato metoda přijímá všechny třídu odvozenou od **System.Object**. Následující příklad vytvoří řetězec ze dvou existujících objektů řetězce a znak dělicí.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **String.Join** metoda vytvoří nový řetězec z pole řetězce a řetězec oddělovače. Tato metoda je užitečná, pokud chcete řetězení více řetězců společně, vytváření seznamu odděleného čárkami.  
  
 Následující příklad používá mezeru pro vazbu pole řetězců.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** metoda vytvoří nový řetězec vložením řetězec na zadané pozici v jiném řetězci. Tato metoda používá index počítaný od nuly. Následující příklad vloží řetězec na pozici indexu páté `MyString` a vytvoří nový řetězec s touto hodnotou.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** metoda zkopíruje části řetězce na pole znaků. Zadaný index začátku řetězce a počet znaků, které se mají zkopírovat. Tato metoda přebírá index zdroje, pole znaků, cílový index a počet znaků pro kopírování. Všechny indexy jsou od nuly.  
  
 Následující příklad používá **CopyTo** metoda kopírování znaků slova "Hello" v řetězci objektu do první pozici indexu pole znaků.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
 [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
