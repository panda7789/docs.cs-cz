---
title: Použití kontraktů dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 28033e3e90c5010eee63f35791b0c3c77e64d1ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59129932"
---
# <a name="using-data-contracts"></a>Použití kontraktů dat
A *kontraktu dat* je oficiální smlouvu mezi službou a klienta, který abstraktně popisuje data, jenž bude vyměněn. To znamená ke komunikaci, klienta a služby nemusíte sdílejí stejné typy stejné kontraktů dat. Přesně definuje kontrakt dat, pro každý parametr nebo návratový typ, jaká data se serializovat (převedena na XML) mají vyměnit.  
  
## <a name="data-contract-basics"></a>Základní kontrakt dat  
 Windows Communication Foundation (WCF) Serializační stroj volá serializátor kontraktu dat ve výchozím nastavení používá k serializaci a deserializaci data (ji převést do a z XML). Všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] primitivní typy, jako jsou celá čísla a řetězce, jakož i určité typy považovány za primitivních elementů, jako například <xref:System.DateTime> a <xref:System.Xml.XmlElement>, lze serializovat s žádný další přípravou a považují se za s kontrakty dat. výchozí. Mnoho [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy také mít stávající smlouvy o data. Úplný seznam Serializovatelné typy, najdete v části [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nová komplexní typy, které vytvoříte, musí mít kontraktu dat definované pro ně být serializovatelný. Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> odvodí kontraktu dat a serializuje všechny veřejně viditelné typy. Všechny vlastnosti veřejné čtení a zápis a pole typu se serializují. Členy z serializace můžete odhlásit pomocí <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Kontrakt dat můžete také explicitně vytvořit pomocí <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy. To se obvykle provádí použitím <xref:System.Runtime.Serialization.DataContractAttribute> atribut typu. Tento atribut lze použít na třídy, struktury a výčty. <xref:System.Runtime.Serialization.DataMemberAttribute> Atribut musí pak použije k jednotlivým členům typ kontraktu dat k označení, že se jedná *datový člen*, to znamená, ho by měly být serializovány. Další informace najdete v tématu [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje smlouvy o poskytování služeb (rozhraní), ke kterému <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy explicitně použít. Příklad ukazuje, že primitivní typy nevyžadují kontraktu dat, zatímco komplexní typ nemá.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 Následující příklad ukazuje, jak kontraktu dat pro `MyTypes.PurchaseOrder` typ je vytvořen s použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy třídy a jejích členů.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Poznámky  
 Následující poznámky k zajištění položek můžete zvážit při vytváření kontraktů dat:  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Atribut zachovaný pouze při použití s zrušeno označení typy. To zahrnuje typy, které nejsou označené s jedním z <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, nebo <xref:System.Runtime.Serialization.EnumMemberAttribute> atributy nebo označen jako serializovatelný jiným způsobem (třeba <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Můžete použít <xref:System.Runtime.Serialization.DataMemberAttribute> atributu na pole a vlastnosti.  
  
-   Úrovně přístupnosti člena (interní, privátní, chráněné nebo veřejný) nemají vliv na kontraktu dat žádným způsobem.  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> Atribut se ignoruje, pokud se použije na statické členy.  
  
-   Během serializace je volána kód vlastnost get pro vlastnost datové členy k získání hodnoty vlastnosti, které mají být serializován.  
  
-   Během deserializace je Neinicializovaný objekt nejprve vytvořen, bez volání žádné konstruktory u typu. Všechny datové členy jsou poté deserializován.  
  
-   Během deserializace se nazývá nastavenou vlastnost kódu pro vlastnost datové členy nastavte vlastnosti na hodnotu deserializován.  
  
-   Pro kontrakt data platná musí být možné k serializaci všechny její datové členy. Úplný seznam Serializovatelné typy, najdete v části [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Obecné typy jsou zpracovány přesně stejným způsobem jako obecné typy. Neexistují žádné zvláštní požadavky na obecné parametry. Zvažte například následující typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Tento typ je serializovatelný, zda typ použitý pro parametr obecného typu (`T`) je serializovatelný, nebo ne. Vzhledem k tomu je potřeba implementovat k serializaci všechny datové členy, následujícího typu je serializovat pouze pokud parametr obecného typu i serializovatelný, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Ukázka kompletní kód služby WCF, který definuje kontrakt dat najdete v článku [základní kontrakt dat](../../../../docs/framework/wcf/samples/basic-data-contract.md) vzorku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Kontrakty dat s dopřednou kompatibilitou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Zpětná volání serializace tolerantní k verzím](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Výchozí hodnoty datových členů](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)
- [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Postupy: Vytvoření základního kontraktu dat pro třídu nebo strukturu](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
