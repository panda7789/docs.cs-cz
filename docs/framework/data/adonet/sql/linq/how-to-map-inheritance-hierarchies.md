---
title: 'Postupy: mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634661"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Postupy: mapování hierarchií dědičnosti
Chcete-li implementovat mapování dědičnosti v technologii LINQ, je nutné zadat atributy a vlastnosti atributu v kořenové třídě hierarchie dědičnosti, jak je popsáno v následujícím postupu. Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k mapování hierarchií dědičnosti. Viz [How to: Configure dědičnost pomocí návrháře o/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
> U podtříd nejsou vyžadovány žádné speciální atributy ani vlastnosti. Všimněte si, že podtřídy nemají atribut <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Mapování hierarchie dědičnosti  
  
1. Přidejte atribut <xref:System.Data.Linq.Mapping.TableAttribute> do kořenové třídy.  
  
2. Také na kořenovou třídu přidejte atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pro každou třídu ve struktuře hierarchie.  
  
3. Pro každý atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> definujte vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Tato vlastnost obsahuje hodnotu, která se zobrazí v databázové tabulce ve sloupci <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>, aby označovala třídu nebo podtřídou, do které tento řádek dat patří.  
  
4. U každého atributu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> přidejte také vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Tato vlastnost obsahuje hodnotu, která určuje třídu nebo podtřídu hodnoty klíče.  
  
5. Pouze na jednom z atributů <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> přidejte vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Tato vlastnost slouží k určení *záložního* mapování, pokud hodnota diskriminátoru z tabulky databáze neodpovídá žádné <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotě v mapování dědičnosti.  
  
6. Přidejte vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pro atribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Tato vlastnost znamená, že se jedná o sloupec, který obsahuje hodnotu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
> Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů ke konfiguraci dědičnosti. Viz [Postupy: Konfigurace dědičnosti pomocí návrháře O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 V následujícím příkladu kódu je `Vehicle` definováno jako kořenová třída a předchozí kroky byly implementovány pro popis hierarchie pro technologii LINQ.  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Podpora dědičnosti](inheritance-support.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](how-to-customize-entity-classes-by-using-the-code-editor.md)
