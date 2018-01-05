---
title: "Přizpůsobení operací pomocí uložené procedury"
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
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5433ef17ec2eec7fe80145a6356d230b9d01a7d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Přizpůsobení operací pomocí uložené procedury
Uložené procedury představují společný přístup k přepsání výchozího nastavení. Příklady v tomto tématu ilustrují, jak můžete vygenerovat metoda obálek pro uložené procedury a jak můžete volat uložené procedury přímo.  
  
 Pokud používáte [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] přiřadit uložené procedury provést vložení, aktualizace a odstranění.  
  
> [!NOTE]
>  Čtení hodnot generovaných zpět na databázi, použijte výstupní parametry v uložené procedury. Pokud nemůžete použít výstupní parametry, zapsat implementace částečné metody aniž byste museli spoléhat na přepsání, které jsou generované [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Členy generované hodnoty musí být nastavena na odpovídající hodnoty po `INSERT` nebo `UPDATE` operace byly úspěšně dokončeny. Další informace najdete v tématu [odpovědnosti vývojáře v přepsání výchozí chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu předpokládáme, že `Northwind` třída obsahuje dvě metody k volání uložené procedury, které jsou používány pro přepsání v odvozené třídě.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující třídy používá tyto metody pro přepsání.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Můžete použít `NorthwindThroughSprocs` přesně tak, jak byste použili `Northwnd`.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Odpovědnosti vývojáře při přepisu výchozího chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
