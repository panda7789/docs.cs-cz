---
title: Použití kontraktů dat
description: Přečtěte si o kontraktu dat, který definuje, pro každý parametr nebo návratový typ, jaká data jsou serializovaná k výměně mezi klientem a serverem WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 80ea2a8bd67c627fbe11ee07e640704c1a41ef7b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244722"
---
# <a name="using-data-contracts"></a>Použití kontraktů dat
*Kontrakt dat* je formální smlouva mezi službou a klientem, která abstraktně popisuje data, která se mají vyměňovat. To znamená, že ke komunikaci klient a služba nemusí sdílet stejné typy, jenom stejné kontrakty dat. Kontrakt dat přesně definuje pro každý parametr nebo návratový typ, jaká data jsou serializovaná (převedená do XML), která se mají vyměňovat.  
  
## <a name="data-contract-basics"></a>Základy kontraktů dat  
 Windows Communication Foundation (WCF) používá ke serializaci a deserializaci dat (převeďte je do a z XML) modul serializace nazývaný serializátor kontraktu dat ve výchozím nastavení. Všechny primitivní typy .NET Framework, jako jsou celá čísla a řetězce, a také určité typy považované za primitivní prvky, jako jsou <xref:System.DateTime> a <xref:System.Xml.XmlElement> , mohou být serializovány bez jiné přípravy a považují se za výchozí kontrakty dat. Mnoho typů .NET Framework také má stávající kontrakty dat. Úplný seznam serializovatelných typů naleznete v tématu [typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md).  
  
 Nové komplexní typy, které vytvoříte, musí mít definici kontraktu dat, aby je bylo možné serializovat. Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> odvodí kontrakt dat a serializace všechny veřejně viditelné typy. Všechny veřejné vlastnosti pro čtení i zápis a pole typu jsou serializovány. Členy můžete odhlásit z serializace pomocí <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> . Kontrakt dat můžete také explicitně vytvořit pomocí <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a. To se obvykle provádí použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu na typ. Tento atribut lze použít pro třídy, struktury a výčty. <xref:System.Runtime.Serialization.DataMemberAttribute>Atribut musí být poté použit pro každého člena typu kontraktu dat, aby označoval, že se jedná o *datový člen*, tedy by měl být serializován. Další informace naleznete v tématu [Serializovatelné typy](serializable-types.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje kontrakt služby (rozhraní), na který byly <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> explicitně aplikovány atributy a. Příklad ukazuje, že primitivní typy nevyžadují kontrakt dat, zatímco komplexní typ dělá.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 Následující příklad ukazuje, jak je vytvořen kontrakt dat pro `MyTypes.PurchaseOrder` typ pomocí <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a pro třídu a její členy.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Poznámky  
 Následující poznámky obsahují položky, které je potřeba vzít v úvahu při vytváření kontraktů dat:  
  
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>Atribut je dodržen pouze při použití s neoznačenými typy. To zahrnuje typy, které nejsou označeny jedním z <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.SerializableAttribute> atributů,, <xref:System.Runtime.Serialization.CollectionDataContractAttribute> , nebo <xref:System.Runtime.Serialization.EnumMemberAttribute> nebo označeny jako serializovatelný jakýmkoli jiným způsobem (například <xref:System.Xml.Serialization.IXmlSerializable> ).  
  
- Atribut lze použít <xref:System.Runtime.Serialization.DataMemberAttribute> pro pole a vlastnosti.  
  
- Úrovně přístupnosti členů (interní, privátní, chráněné nebo veřejné) neovlivňují kontrakt dat jakýmkoli způsobem.  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute>Atribut je ignorován, pokud je použit pro statické členy.  
  
- Během serializace je pro datové členy vlastnosti volána vlastnost-get Code pro získání hodnoty vlastností, které mají být serializovány.  
  
- Během deserializace je nejprve vytvořen Neinicializovaný objekt, aniž by bylo nutné volat žádné konstruktory typu. Pak jsou všechny datové členy deserializovány.  
  
- Během deserializace je pro datové členy vlastností volán kód sady vlastností pro nastavení vlastností na hodnotu deserializovat.  
  
- Aby byl kontrakt dat platný, musí být možné serializovat všechny jeho datové členy. Úplný seznam serializovatelných typů naleznete v tématu [typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md).  
  
     Obecné typy jsou zpracovávány přesně stejným způsobem jako neobecné typy. Pro obecné parametry neexistují žádné zvláštní požadavky. Zvažte například následující typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Tento typ je serializovatelný bez ohledu na to, zda typ použitý pro parametr obecného typu ( `T` ) je serializovatelný nebo nikoli. Vzhledem k tomu, že musí být možné serializovat všechny datové členy, je následující typ serializovatelný pouze v případě, že parametr obecného typu je také serializovatelný, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Kompletní vzorek kódu služby WCF, který definuje kontrakt dat, najdete v ukázce [základního Data Contract](../samples/basic-data-contract.md) .  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Serializovatelné typy](serializable-types.md)
- [Názvy kontraktu dat](data-contract-names.md)
- [Ekvivalence kontraktů dat](data-contract-equivalence.md)
- [Pořadí datových členů](data-member-order.md)
- [Známé typy kontraktů dat](data-contract-known-types.md)
- [Kontrakty dat s dopřednou kompatibilitou](forward-compatible-data-contracts.md)
- [Správa verzí kontraktů dat](data-contract-versioning.md)
- [Zpětná volání serializace tolerantní k verzím](version-tolerant-serialization-callbacks.md)
- [Výchozí hodnoty datových členů](data-member-default-values.md)
- [Typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md)
- [Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
