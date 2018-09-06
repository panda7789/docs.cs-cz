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
ms.openlocfilehash: 477791a0d62186b6cb88d0fae3aa9b4e38b3ef35
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870107"
---
# <a name="creating-new-strings-in-net"></a>Vytváření nových řetězců v .NET
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Umožňuje řetězců, které mají být vytvořené pomocí jednoduchého přiřazení a také přetížení konstruktoru třídy pro podporu vytváření řetězců pomocí několika různých parametrů. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také poskytuje několik metod <xref:System.String?displayProperty=nameWithType> třídu, která vytvořit nový řetězec kombinací několika řetězcích, polích řetězce, objekty nebo objekty.  
  
## <a name="creating-strings-using-assignment"></a>Vytváření řetězců pomocí přiřazení  
 Nejjednodušší způsob, jak vytvořit novou <xref:System.String> objekt slouží k přiřazení řetězcový literál <xref:System.String> objektu.  
  
## <a name="creating-strings-using-a-class-constructor"></a>Vytváření řetězců pomocí konstruktoru třídy  
 Můžete použít přetížení <xref:System.String> konstruktoru třídy pro vytvoření řetězce z pole znaků. Můžete také vytvořit nový řetězec tak, že duplikujete určitý znak zadaného počtu opakování.  
  
## <a name="methods-that-return-strings"></a>Metody, které vracejí řetězce  
 Následující tabulka uvádí několik užitečných metod, které vrací nové objekty.  
  
|Název metody|Použití|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|Vytvoří na základě sady vstupních objektů formátovaný řetězec.|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|Vytvoří řetězce ze dvou nebo více řetězců.|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|Vytvoří nový řetězec kombinací pole řetězců.|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|Vytvoří nový řetězec vložením řetězce do určeného indexu existujícího řetězce.|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|Zkopíruje do zadané pozice v poli znaků zadané znaky v řetězci.|  
  
### <a name="format"></a>Formát  
 Můžete použít **String.Format** metodu pro vytvoření formátovaných řetězců a řetězit řetězce představující více objektů. Libovolný objekt předaný této metodě automaticky převede na řetězec. Například, pokud aplikace vyžaduje zobrazení **Int32** hodnotu a **data a času** hodnotu pro uživatele, můžete snadno sestavit řetězec představující tyto hodnoty pomocí **formátu**metody. Informace o formátování konvence tuto metodu použít, najdete v části na [složené formátování](../../../docs/standard/base-types/composite-formatting.md).  
  
 V následujícím příkladu **formátu** metodu pro vytvoření řetězce, který používá proměnnou celého čísla.  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 V tomto příkladu<xref:System.DateTime.Now%2A?displayProperty=nameWithType> zobrazuje aktuální datum a čas způsobem určené jazykové verze přidružené k aktuální vlákno.  
  
### <a name="concat"></a>concat  
 **String.Concat** metodu je možné snadno vytvořit nový objekt řetězce ze dvou nebo více existujících objektů. Poskytuje nezávislým na jazyku způsob, jak zřetězení řetězců. Tato metoda přijímá jakoukoli třídu, která je odvozena z **System.Object**. Následující příklad vytvoří řetězec ze dvou existujících řetězcových objektů a oddělovacích znaků.  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a>Join  
 **String.Join** metoda vytvoří nový řetězec z pole řetězců a oddělovacího řetězce. Tato metoda je užitečná, pokud chcete řetězení více řetězců společně, vytvoření seznamu odděleného čárkami.  
  
 Následující příklad používá mezeru vytvořit vazbu pole řetězců.  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a>Insert  
 **String.Insert** metoda vytvoří nový řetězec vložením řetězce do zadané pozice v jiném řetězci. Tato metoda používá index založený na nule. V následujícím příkladu vloží řetězec na páté index pozice `MyString` a vytvoří nový řetězec s touto hodnotou.  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a>CopyTo  
 **String.CopyTo** metoda zkopíruje částí řetězce na pole znaků. Můžete určit index začátku řetězce a počet znaků, které se mají zkopírovat. Tato metoda přebírá index zdroje, pole znaků, cílový index a počet znaků, které mají kopírovat. Všechny indexy jsou počítány od nuly.  
  
 V následujícím příkladu **CopyTo** metoda kopírování znaků slova "Hello" v řetězci objektu na první pozici indexu pole znaků.  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Základní operace s řetězci](../../../docs/standard/base-types/basic-string-operations.md)  
- [Složené formátování](../../../docs/standard/base-types/composite-formatting.md)
