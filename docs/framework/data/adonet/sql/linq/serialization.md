---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: bf303f9a79fbcab85d33fcb3ebb132d1d3e2041d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781108"
---
# <a name="serialization"></a>Serializace
Toto téma popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] možnosti serializace. Následující odstavce obsahují informace o tom, jak přidat serializace během generování kódu v době návrhu a chování [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] serializace v době běhu tříd.  
  
 Můžete přidat kód serializace v době návrhu některou z následujících metod:  
  
- V Návrhář relací objektů změňte vlastnost **režim serializace** na **jednosměrný**.  
  
- Do příkazového řádku SQLMetal přidejte možnost **/Serialization** . Další informace naleznete v tématu [SqlMetal. exe (Nástroj pro generování kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Kód vygenerovaný službou [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje ve výchozím nastavení odložené možnosti načítání. Odložené načítání je velmi praktické na střední úrovni pro transparentní načítání dat na vyžádání. Je však problematické pro serializaci, protože triggery triggeru odvodily, zda je odložené načtení určeno nebo nikoli. V důsledku toho, když je objekt serializován, je serializovaný uzavřený uzávěr v rámci všech odchozích odkazů, které jsou načteny odloženy.  
  
 Funkce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] serializace řeší tento problém hlavně prostřednictvím dvou mechanismů:  
  
- Režim pro vypnutí odloženého načítání (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). <xref:System.Data.Linq.DataContext> Další informace naleznete v tématu <xref:System.Data.Linq.DataContext>.  
  
- Přepínač pro generování kódu pro generování <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributy u generovaných entit. Tento aspekt, včetně chování tříd odloženého načítání, je v rámci serializace hlavním předmětem tohoto tématu.  
  
### <a name="definitions"></a>Definice  
  
- *Serializátor kontraktu DataContract*: Výchozí serializátor používaný komponentou WCF (Windows Communication Framework) v .NET Framework 3,0 nebo novějších verzích.  
  
- *Jednosměrná serializace*: Serializovaná verze třídy, která obsahuje pouze jednosměrnou vlastnost Association (pro zamezení cyklu). Podle konvence je vlastnost na nadřazené straně vztahu primárního cizího klíče označena k serializaci. Druhá strana v obousměrném přidružení není serializován.  
  
     Jednosměrná serializace je jediným typem serializace, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kterou podporuje.  
  
## <a name="code-example"></a>Příklad kódu  
 Následující kód používá tradiční `Customer` třídy a `Order` z ukázkové databáze Northwind a ukazuje, jak jsou tyto třídy upraveny pomocí atributů serializace.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Pro třídu v následujícím příkladu je pro zkrácení zobrazena pouze vlastnost zpětného přidružení odpovídající `Customer` třídě. `Order` <xref:System.Runtime.Serialization.DataMemberAttribute> Nemá atribut, aby se zabránilo cyklu.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Postup serializace entit  
 Entity můžete serializovat v kódech uvedených v předchozí části následujícím způsobem:  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Samočinné rekurzivní relace  
 Relace s samočinným rekurzivním zpracováním se řídí stejným vzorem. Vlastnost Association odpovídající cizímu klíči <xref:System.Runtime.Serialization.DataMemberAttribute> neobsahuje atribut, zatímco nadřazená vlastnost dělá.  
  
 Vezměte v úvahu následující třídu, která má dva samočinně rekurzivní relace: Employee. Manager/Reports a Employee. instruktor/mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- [Základní informace](background-information.md)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [Postupy: Vytváření entit serializovatelných](how-to-make-entities-serializable.md)
