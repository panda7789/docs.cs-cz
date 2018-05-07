---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: cc299e26316b1a3a6fd9b475dcdb8e3911bcf2e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="serialization"></a>Serializace
Toto téma popisuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] možnosti serializace. Odstavce, které následují poskytují informace o tom, jak přidat serializace během generování kódu v době návrhu a chování běhové serializace [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] třídy.  
  
 Můžete přidat serializace kódu v době návrhu a to buď z následujících metod:  
  
-   V [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], změnit **serializace režimu** vlastnost **Unidirectional**.  
  
-   Na SQLMetal příkazového řádku, přidejte **/serialization** možnost. Další informace najdete v tématu [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Přehled  
 Kód vygenerovaný [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] poskytuje odložené načítání možnosti ve výchozím nastavení. Odložené načtení je velmi vhodné na střední vrstvě pro transparentní načítání dat na vyžádání. Je však problematické pro serializaci, protože serializátor aktivuje odložené načítání, zda je určený odložené načítání, nebo ne. Platí když je objekt serializován, jeho přechodné uzavření v seznamu všechny odchozí odkazy odložení načíst serializován.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Serializace funkce řeší tento problém, primárně prostřednictvím dvou mechanismů:  
  
-   A <xref:System.Data.Linq.DataContext> režim pro vypnutí odložené načítání (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>). Další informace naleznete v tématu <xref:System.Data.Linq.DataContext>.  
  
-   Generování kódu přepínač ke generování <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> atributy u vygenerované entit. Tento aspekt, včetně chování odložené načítání tříd pod serializace, je hlavní téma tohoto tématu.  
  
### <a name="definitions"></a>Definice  
  
-   *Serializátor kontraktu*: výchozí serializátor používaný připojením komponenta Windows Communication Framework (WCF) na rozhraní .NET Framework 3.0 nebo novější verze.  
  
-   *Jednosměrný serializace*: serializovaná verze třídu, která obsahuje jenom jednosměrný přidružení vlastnost (aby se zabránilo cyklus). Podle konvence je vlastnost na straně nadřazené primární cizího klíče relace označen pro serializaci. Druhá strana přidružení obousměrného není serializovat.  
  
     Jednosměrný serializace je pouze typ serializace nepodporuje [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
## <a name="code-example"></a>Příklad kódu  
 Následující kód používá tradiční `Customer` a `Order` třídy z ukázková databáze Northwind a ukazuje, jak jsou tyto třídy dekorované s atributy serializace.  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 Pro `Order` třídy v následujícím příkladu pouze vlastnosti zpětné přidružení odpovídající `Customer` třídy se zobrazí jako stručný výtah. Nemá `DataMember` atribut, aby se zabránilo cyklický odkaz.  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>Tom, jak serializovat entity  
 Může serializovat entity v kódy, které jsou uvedeny v předchozí části takto:  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>Samoobslužné rekurzivní relace  
 Samoobslužné rekurzivní relace postupují stejným způsobem. Vlastnosti přidružení odpovídající cizí klíč nemá `DataMember` atribut, zatímco nemá nadřazený klíč.  
  
 Vezměte v úvahu následující třídy, která má dvě relace samoobslužné rekurzivní: Employee.Manager/Reports a Employee.Mentor/Mentees.  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 [Základní informace](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [SqlMetal.exe (nástroj pro vytváření kódu)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [Postupy: Nastavení entit jako serializovatelných](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
