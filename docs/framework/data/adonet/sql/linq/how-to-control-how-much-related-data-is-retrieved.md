---
title: 'Postupy: Určení objemu načítaných souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782063"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Postupy: Určení objemu načítaných souvisejících dat
<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Použijte metodu k určení, která data související s vaším hlavním cílem by měla být načtena ve stejnou dobu. Pokud například víte, že budete potřebovat informace o objednávkách zákazníků, můžete použít <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> k tomu, abyste se ujistili, že informace o objednávkách budou načteny ve stejnou dobu jako informace o zákaznících. Tento přístup má za následek pouze jednu cestu k databázi pro obě sady informací.  
  
> [!NOTE]
> Data související s hlavním cílem dotazu můžete načíst načtením více produktů jako jedné velké projekce, jako je například načítání objednávek při cílení na zákazníky. Ale tento přístup má často nevýhody. Například výsledky jsou pouze projekce, nikoli entity, které lze změnit a zachovat pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. A můžete načíst spoustu dat, která nepotřebujete.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou při spuštění dotazu `Orders` načteny všechny `Customers` , které jsou umístěny v Londýně. V důsledku toho se po úspěšném přístupu k `Orders` vlastnosti `Customer` objektu neaktivuje nový databázový dotaz.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Dotazování na databázi](querying-the-database.md)
