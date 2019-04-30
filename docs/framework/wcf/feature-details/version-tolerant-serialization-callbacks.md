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
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932623"
---
# <a name="version-tolerant-serialization-callbacks"></a>Zpětná volání serializace tolerantní k verzím
Programovací model kontraktu dat plně podporuje metody zpětného volání serializace tolerantní, který <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy podporu.  
  
## <a name="version-tolerant-attributes"></a>Verze chybám atributy  
 Existují čtyři atributy zpětného volání. Každý atribut lze použít pro metodu, která volá modul pro serializaci nebo deserializaci v různých časech. Následující tabulka vysvětluje, kdy používat jednotlivé atributy.  
  
|Atribut|Když je volána odpovídající – metoda|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Volá se před serializací typu.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Volá se po serializaci typu.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Volá se před deserializace typu.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Volá se po deserializace typu.|  
  
 Metody, musíte přijmout <xref:System.Runtime.Serialization.StreamingContext> parametru.  
  
 Tyto metody jsou primárně určeny pro použití se službou správy verzí nebo inicializace. Během deserializace nejsou volány žádné konstruktory. Proto se datové členy nemusí být správně inicializován (na určený výchozí hodnoty) Pokud jsou data pro tyto členy, chybí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typu, který chybí některé datové členy. Když to pokud chcete opravit, použijte metodu zpětného volání označenou pomocí <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak je znázorněno v následujícím příkladu.  
  
 Můžete označit jenom jednu metodu na typ s každým z předchozí atributy zpětného volání.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serializace tolerantní vůči verzím (VTS)](../../../../docs/standard/serialization/version-tolerant-serialization.md)
