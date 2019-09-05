---
title: Přizpůsobení operací pomocí uložených procedur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
ms.openlocfilehash: 63f4cb3cbb90afc37629b336972b5e09d20346b3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247532"
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Přizpůsobení operací pomocí uložených procedur
Uložené procedury reprezentují běžný přístup k přepsání výchozího chování. Příklady v tomto tématu ukazují, jak lze použít vygenerované obálky metody pro uložené procedury a jak lze přímo volat uložené procedury.  
  
 Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů k přiřazení uložených procedur k provádění vložení, aktualizace a odstranění.  
  
> [!NOTE]
> Chcete-li načíst zpět hodnoty generované databází, použijte výstupní parametry v uložených procedurách. Pokud nemůžete použít výstupní parametry, zapište implementaci částečné metody namísto spoléhání na přepisy vygenerované Návrhář relací objektů. Členy mapované na hodnoty generované databází musí být po `INSERT` `UPDATE` úspěšném dokončení operací nastaveny na příslušné hodnoty. Další informace najdete v tématu [zodpovědnosti vývojáře při přepisu výchozího chování](responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 V následujícím příkladu Předpokládejme, že `Northwind` třída obsahuje dvě metody pro volání uložených procedur, které jsou používány pro přepsání v odvozené třídě.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující třída používá tyto metody pro přepsání.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Můžete použít `NorthwindThroughSprocs` přesně tak, jak budete používat `Northwnd`.  
  
### <a name="code"></a>Kód  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Odpovědnosti vývojáře při přepisu výchozího chování](responsibilities-of-the-developer-in-overriding-default-behavior.md)
