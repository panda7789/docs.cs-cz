---
title: Zpětná volání serializace tolerantní k verzím
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
ms.openlocfilehash: 0736f94b1fe1a91b20ee76da673e0bc139aa802a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959558"
---
# <a name="version-tolerant-serialization-callbacks"></a>Zpětná volání serializace tolerantní k verzím
Model programování kontraktů dat plně podporuje metody zpětného volání serializace odolné proti <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> verzí <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> , které třídy a podporují.  
  
## <a name="version-tolerant-attributes"></a>Atributy odolné vůči verzím  
 Existují čtyři atributy zpětného volání. Každý atribut lze použít na metodu, kterou modul serializace/deserializace volá v různých časech. Následující tabulka vysvětluje, kdy použít jednotlivé atributy.  
  
|Atribut|Při volání odpovídající metody|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Volá se před serializací typu.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Volá se po serializaci typu.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Volá se před deserializací typu.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Volá se po deserializaci typu.|  
  
 Metody musí přijmout <xref:System.Runtime.Serialization.StreamingContext> parametr.  
  
 Tyto metody jsou primárně určeny pro použití se správou verzí nebo inicializací. Během deserializace nejsou volány žádné konstruktory. Datové členy proto nemusí být správně inicializovány (na zamýšlené výchozí hodnoty), pokud data pro tyto členy chybějí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typu, ve kterém chybí některé datové členy. Chcete-li tento problém vyřešit, použijte metodu zpětného <xref:System.Runtime.Serialization.OnDeserializingAttribute>volání označenou, jak je znázorněno v následujícím příkladu.  
  
 U každého z předchozích atributů zpětného volání můžete označit jenom jednu metodu na typ.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serializace tolerantní vůči verzím (VTS)](../../../standard/serialization/version-tolerant-serialization.md)
