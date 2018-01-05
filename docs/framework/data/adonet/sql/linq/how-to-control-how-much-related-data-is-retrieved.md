---
title: "Postupy: řízení, kolik související Data načtena"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b35c6e4bcb316823a42dc8501fa08df5a87f3275
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Postupy: řízení, kolik související Data načtena
Použití <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metoda k určení, která data související s vaší hlavní cíl mají být načtena ve stejnou dobu. Například pokud jste si jisti, budete potřebovat informace o objednávek zákazníků, můžete použít <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> a ujistěte se, že je ve stejnou dobu jako informace o zákazníkovi načíst informace o objednávce. Tento přístup je výsledkem pouze jediná cesta k databázi pro obě sady informace.  
  
> [!NOTE]
>  Můžete načíst data související s hlavním cílem tohoto dotazu načtením smíšený produkt jako jeden velký projekce, jako je například získávání objednávky po cíle zákazníků. Ale tento přístup má často nevýhody. Například výsledky jsou právě projekce a není entit, které můžete změnit a ve uchováván [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. A může být načítání velké množství dat, který není nutné.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu všechny `Orders` pro všechny `Customers` kdo jsou umístěny v Londýně se načítají, když je proveden dotaz. V důsledku toho následných přístup k `Orders` vlastnost `Customer` objekt neaktivuje nový databázový dotaz.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Dotazování na databázi](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
