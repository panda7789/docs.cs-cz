---
title: Přizpůsobení operací pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: d9f8d15b46f6e5575bd206bf572ffda0365e58f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743549"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Přizpůsobení operací pomocí uložených procedur
Uložených procedur představují běžný postup k přepisování výchozího chování. Příklady v tomto tématu ilustrují, jak můžete generovat obálky metody pro uložené procedury a jak vám uložené procedury lze volat přímo.  
  
 Pokud používáte Visual Studio, můžete použít Návrháře relací objektů přiřazení uložených procedur za účelem vložení, aktualizace a odstranění.  
  
> [!NOTE]
>  Načíst hodnoty zpět databáze vygenerovala, použijte výstupních parametrů v uložených procedurách. Pokud nemůžete použít výstupních parametrů, zápis přepsání implementace částečné metody, aniž byste museli spoléhat na vygenerovaný Návrhář relací objektů. Databáze vygenerovala hodnoty členů musí být nastaven na odpovídající hodnoty po `INSERT` nebo `UPDATE` operace byly úspěšně dokončeny. Další informace najdete v tématu [odpovědnosti pro vývojáře v přepisuje výchozí chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu se předpokládá, že `Northwind` třída obsahuje dvě metody k volání uložené procedury, které se používají pro přepsání v odvozené třídě.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Odpovědnosti vývojáře při přepisu výchozího chování](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
