---
title: "Použití kontraktů dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acbe1fc52cec011863dea8f3ae81492e3661cd97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-data-contracts"></a>Použití kontraktů dat
A *kontrakt dat* formální dohodu mezi službou a klienta, který abstraktně popisuje data, která mají být vyměňují. To znamená komunikovat, klient a služba nemají sdílet stejné typy stejné kontrakty dat. Přesněji definuje kontrakt dat, pro každý parametr nebo návratový typ, jaká data se serializovat (převedena na XML) k výměně.  
  
## <a name="data-contract-basics"></a>Základy kontraktu dat  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]modul serializace názvem serializátor kontraktu dat ve výchozím nastavení se používá k serializaci a deserializaci dat (ji převést do a z XML). Všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] primitivní typy, jako je celá čísla a řetězce, a také některé typy zacházet jako primitiva, například <xref:System.DateTime> a <xref:System.Xml.XmlElement>, lze serializovat bez další přípravy a jsou považovány za tak, že má kontrakty dat výchozí. Mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy také mít kontrakty existující data. Úplný seznam Serializovatelné typy najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nové komplexní typy, které vytvoříte, musí mít kontraktu dat definované mohly být serializovatelný. Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> odvodí kontrakt dat a serializuje všechny typy veřejně viditelný. Všechny veřejné vlastnosti a pole typu se serializují. Můžete chodit členy z serializace pomocí <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Kontrakt dat můžete vytvořit také explicitně pomocí <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy. To se obvykle provádí s použitím <xref:System.Runtime.Serialization.DataContractAttribute> atributu typu. Tento atribut lze použít k tříd, struktur a výčty. <xref:System.Runtime.Serialization.DataMemberAttribute> Atributu se musí pak použít pro každého člena typu kontraktu dat, to znamená, že je *– datový člen*, to znamená, že ho by měly být serializovány. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje kontraktu služby (rozhraní), ke kterému <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> explicitně použít atributů. Příklad ukazuje, že primitivní typy nevyžadují kontraktu dat při nemá komplexního typu.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 Následující příklad ukazuje, jak kontraktu dat pro `MyTypes.PurchaseOrder` se vytvoří typ použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a její členy.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Poznámky  
 Následující poznámky k obsahují položky, které je třeba zvážit při vytváření kontrakty dat:  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Atribut je dodržení pouze při použití s zrušit označení typy. To zahrnuje typy, které nejsou označené s jedním z <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, nebo <xref:System.Runtime.Serialization.EnumMemberAttribute> atributy nebo označen jako serializovatelný jinými prostředky (například <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atribut polí a vlastností.  
  
-   Úrovně přístupnosti člena (interní, privátní, chráněný nebo veřejný) nemají vliv kontrakt dat, jakýmkoli způsobem.  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> Atribut je ignorována, pokud je tato statické členy.  
  
-   Během serializace se nazývá kód vlastnost get pro vlastnost datové členy k získání hodnoty vlastnosti, které chcete serializovat.  
  
-   Během deserializace je k neinicializovanému objektu nejprve vytvořen, bez volání žádné konstruktory typu. Všichni členové data jsou poté deserializován.  
  
-   Během deserializace je sada vlastností kód volat pro vlastnost datových členů a nastavte vlastnosti na hodnotu deserializován.  
  
-   Pro kontrakt data platná musí být možné serializovat všechny její členy data. Úplný seznam Serializovatelné typy najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Obecné typy jsou zpracovávány v přesně stejně jako typy neobecnou. Neexistují žádné zvláštní požadavky pro obecné parametry. Zvažte například následující typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Tento typ je serializovatelný jestli typ použitý pro parametr obecného typu (`T`) je serializovatelný, nebo ne. Protože musí být možné serializovat všechny datové členy, následující typ je serializovatelný pouze pokud parametr obecného typu je také serializable, a jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Ukázka dokončení kódu služby WCF, který definuje kontrakt dat najdete v článku [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md) ukázka.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Názvy kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Kontrakty dat s dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Zpětná volání serializace tolerantní k verzi](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Vychozí hodnoty datových členů](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [Typy podporované systémem serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [Postupy: vytvoření kontraktu základní Data pro třídu nebo strukturu](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
