---
title: 'Postupy: Mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: ad945cfe476441a92e8af9527b08e66f3e6e52c1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734023"
---
# <a name="how-to-map-inheritance-hierarchies"></a>Postupy: Mapování hierarchií dědičnosti
Implementace dědičnosti mapování v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], musíte zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti jak je popsáno v následujících krocích. Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapování hierarchií dědičnosti. Zobrazit [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  V podtříd jsou požadována žádná speciální atributy nebo vlastnosti. Mějte na paměti zvlášť, podtřídy nemají <xref:System.Data.Linq.Mapping.TableAttribute> atribut.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Mapování hierarchie dědičnosti  
  
1.  Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut kořenový třídy.  
  
2.  Také do kořenové třídy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut pro každou třídu ve struktuře hierarchie.  
  
3.  Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, definovat <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která se zobrazí v tabulce databáze <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sloupec, aby označoval, které třída nebo podtřídou tento řádek dat patří do.  
  
4.  Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, také přidat <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která určuje, které třída nebo podtřídou označuje hodnotu klíče.  
  
5.  Pouze na jednom z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atributy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> vlastnost.  
  
     Tato vlastnost slouží k určení *záložní* mapování, když hodnota diskriminátoru z databázové tabulky neodpovídá žádnému <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu v mapování dědičnosti.  
  
6.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
     Tato vlastnost znamená, že se jedná o sloupec, který obsahuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] konfigurace dědičnosti. Zobrazit [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 V následujícím příkladu kódu `Vehicle` je definován jako kořenová třída a byly implementovány v předchozích krocích k popisu hierarchii [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také:
- [Podpora dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
