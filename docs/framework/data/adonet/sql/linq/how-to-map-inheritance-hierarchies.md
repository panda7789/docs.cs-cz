---
title: 'Postupy: mapování hierarchie dědičnosti'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 4ffc3e9e7b9c5cc52f5f6fb5cbefd279ca1c0505
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-map-inheritance-hierarchies"></a>Postupy: mapování hierarchie dědičnosti
K implementaci dědičnosti mapování v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], musíte zadat atributy a vlastností atributu na kořenová třída hierarchie dědičnosti jak je popsáno v následujících krocích. Vývojáři pomocí sady Visual Studio můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] k mapování hierarchie dědičnosti. V tématu [postupy: Konfigurace dědičnosti pomocí Návrhář relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
> [!NOTE]
>  Žádné speciální atributy nebo vlastnosti je nutné podtřídách. Zejména Všimněte si, že podtřídy nemají <xref:System.Data.Linq.Mapping.TableAttribute> atribut.  
  
### <a name="to-map-an-inheritance-hierarchy"></a>Pro mapování hierarchie dědičnosti  
  
1.  Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut kořenová třída.  
  
2.  Také do kořenové třídy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut pro každou třídu ve struktuře hierarchie.  
  
3.  Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, definování <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která se zobrazí v tabulce databáze v <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sloupce k určení, které třídy nebo podtřídou tento řádek dat patří.  
  
4.  Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, také přidat <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> vlastnost.  
  
     Tato vlastnost obsahuje hodnotu, která určuje, které třídy nebo podtřídou označuje hodnotu klíče.  
  
5.  Pouze na jednom z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atributy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> vlastnost.  
  
     Tato vlastnost slouží k určení *záložní* mapování při diskriminátoru hodnotu z tabulky databáze neodpovídá žádnému <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnota mapování dědičnosti.  
  
6.  Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.  
  
     Tato vlastnost označuje, že toto je sloupec, který obsahuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
  
> [!NOTE]
>  Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] konfigurace dědičnosti. V tématu [postupy: Konfigurace dědičnosti pomocí Návrhář relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 V následujícím příkladu kódu `Vehicle` je definován jako kořenová třída a provedení předchozí kroky k popisu hierarchii [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Podpora dědičnosti](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [Postupy: Přizpůsobení tříd entit pomocí editoru kódu](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
