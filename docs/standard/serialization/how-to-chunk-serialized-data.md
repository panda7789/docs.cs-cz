---
title: 'Postupy: bloku dat serializovaná data'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 65e332d229da8fe51ad9c3e9850603471b1dfb12
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307233"
---
# <a name="how-to-chunk-serialized-data"></a>Postupy: bloku dat serializovaná data

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Jsou dva problémy, k nimž došlo při odesílání velkých sad dat do webové služby zpráv:  
  
1. Velké pracovní sada (paměť) z důvodu ukládání do vyrovnávací paměti modul serializace.  
  
2. Nadměrné využití šířky pásma vzhledem k inflaci 33 procent po kódování Base64.  
  
 Chcete-li tyto problémy vyřešit, implementovat <xref:System.Xml.Serialization.IXmlSerializable> rozhraní pro řízení serializace a deserializace. Konkrétně implementovat <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody k bloku dat data.  
  
### <a name="to-implement-server-side-chunking"></a>K implementaci bloků na straně serveru  
  
1. V počítači serveru musí vypnout ukládání do vyrovnávací paměti technologie ASP.NET a návratový typ, který implementuje metodu webové <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2. Typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> chunks data v <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.  
  
### <a name="to-implement-client-side-processing"></a>K implementaci zpracování na straně klienta  
  
1. Změnit metodu webové na proxy serveru klienta má být vrácen typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable>. Můžete použít <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> k provést automaticky, ale není to zde uvedeny.  
  
2. Implementace <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodu za účelem čtení blokového data datového proudu a zápis na disk bajtů. Tato implementace také vyvolává průběh události, které mohou být využívána grafického ovládacího prvku, jako je například indikátor průběhu.  
  
## <a name="example"></a>Příklad  
Následující příklad kódu ukazuje metodu webové na straně klienta, který vypne ukládání do vyrovnávací paměti technologie ASP.NET. Profil také ukazuje na straně klienta provádění <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, které chunks data v <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilování kódu  
  
-   Kód používá následující obory názvů: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, a <xref:System.Xml.Schema>.  
  
## <a name="see-also"></a>Viz také:

- [Vlastní serializace](custom-serialization.md)
