---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 56ebe888b816972f8d72873e4fca9f5204e6c772
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408922"
---
# <a name="serialization"></a>Serializace
Toto téma popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] možnosti serializace. Odstavců, které následují poskytují informace o tom, jak přidat serializace při generování kódu v době návrhu a chování za běhu serializace [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] třídy.  
  
 Můžete přidat serializačního kódu v době návrhu jeden z následujících metod:  
  
-   V [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], změnit **režim serializace** vlastnost **jednosměrný**.  
  
-   Na příkazovém řádku SQLMetal přidejte **/serialization** možnost. Další informace najdete v tématu [SqlMetal.exe (nástroj pro generování kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Kód vygenerovaný [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje možnosti pro odložené načítání ve výchozím nastavení. Odložené načítání je velmi vhodné na střední vrstvě pro transparentní načtení dat na vyžádání. Je však problematické pro serializaci, protože serializátoru, který se aktivuje odložené načítání, jestli je určený pro odložené načítání, nebo ne. V důsledku toho pokud je objekt serializován, jeho tranzitivní uzavření v seznamu všechny odchozí odkazy pozdržet načtené serializován.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Serializace funkce řeší tento problém, primárně prostřednictvím dvou mechanismů:  
  
-   A <xref:System.Data.Linq.DataContext> režimu pro vypnutí odloženého načítání (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Další informace naleznete v tématu <xref:System.Data.Linq.DataContext>.  
  
-   Generování kódu přepínače ke generování <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributy u vygenerované entit. Tento aspekt, včetně chování odložit načítání tříd v části serializace, je hlavní předmětem tohoto tématu.  
  
### <a name="definitions"></a>Definice  
  
-   *Serializátor kontraktu dat DataContract*: Výchozí serializátor používaný připojením komponentu Windows Communication Framework (WCF) na rozhraní .NET Framework 3.0 nebo novější verze.  
  
-   *Jednosměrný serializace*: Serializovaná verze třídu, která obsahuje pouze jednosměrná přidružení vlastnosti (aby se zabránilo cyklus). Vlastnost u nadřazené straně vztahu primární cizího klíče je podle konvence označen pro serializaci. Druhé straně obousměrné přidružení není provedena.  
  
     Jednosměrný serializace je jediný typ serializace nepodporuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Příklad kódu  
 Následující kód používá tradiční `Customer` a `Order` třídy z ukázkové databáze Northwind a ukazuje, jak tyto třídy jsou vybaveny atributy serializace.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Pro `Order` třídy v následujícím příkladu, pouze vlastnost reverzní přidružení odpovídající `Customer` je například pro zkrácení. Nemá <xref:System.Runtime.Serialization.DataMemberAttribute> atribut, aby se zabránilo cyklus.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Jak k serializaci entit  
 Může serializovat entit v kódu je znázorněno v předchozí části takto:  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Self rekurzivní relace  
 Self rekurzivní relace postupují stejným způsobem. Vlastnost přidružení cizího klíče odpovídající nemá <xref:System.Runtime.Serialization.DataMemberAttribute> atribut, že nadřazená vlastnost nepodporuje.  
  
 Vezměte v úvahu následující třídy, která obsahuje dvě self rekurzivní relace: Employee.Manager/Reports a Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Viz také:
- [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [Postupy: Nastavení entit jako serializovatelných](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
