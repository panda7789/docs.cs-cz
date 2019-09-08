---
title: 'Postupy: Mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1366e8f5f79a8e695e52c405e20a894861453ae7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781778"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Postupy: Mapování hierarchií dědičnosti
Chcete-li implementovat mapování [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]dědičnosti v nástroji, je nutné zadat atributy a vlastnosti atributu pro kořenovou třídu Hierarchie dědičnosti, jak je popsáno v následujícím postupu. Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k mapování hierarchií dědičnosti. Viz [jak: Nakonfigurujte dědičnost pomocí návrháře](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)O/R.  
  
> [!NOTE]
> U podtříd nejsou vyžadovány žádné speciální atributy ani vlastnosti. Všimněte si, že podtřídy <xref:System.Data.Linq.Mapping.TableAttribute> nemají atribut.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Mapování hierarchie dědičnosti  
  
1. <xref:System.Data.Linq.Mapping.TableAttribute> Přidejte atribut do kořenové třídy.  
  
2. Také pro kořenovou třídu přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut pro každou třídu v hierarchii struktury.  
  
3. Pro každý <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> definujte vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která se zobrazí v databázové tabulce ve <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sloupci, aby označovala třídu nebo podtřídu, do které tento řádek dat patří.  
  
4. Pro každý <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut také <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> přidejte vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která určuje třídu nebo podtřídu hodnoty klíče.  
  
5. Pouze v jednom z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atributů <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> přidejte vlastnost.  
  
     Tato vlastnost slouží k určení *záložního* mapování, pokud hodnota diskriminátoru z tabulky databáze neodpovídá žádné <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotě v mapování dědičnosti.  
  
6. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> pro atribut.  
  
     Tato vlastnost znamená, že se jedná o sloupec, který obsahuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů ke konfiguraci dědičnosti. Viz [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 V následujícím příkladu `Vehicle` kódu je definován jako kořenová třída a předchozí kroky byly implementovány pro popis hierarchie pro [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Podpora dědičnosti](inheritance-support.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
