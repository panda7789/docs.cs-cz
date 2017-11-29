---
title: "Zpětná volání serializace tolerantní k verzím"
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
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7c00cadd4b0e643e35f7f56a28760e261c423699
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="version-tolerant-serialization-callbacks"></a>Zpětná volání serializace tolerantní k verzím
Programovací model kontraktu dat plně podporuje metody zpětného volání serializace tolerantní k verzi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy podpory.  
  
## <a name="version-tolerant-attributes"></a>Verze proti chybám atributy  
 Existují čtyři atributy zpětného volání. Každý atribut je použít pro metodu, která volá modul serializaci nebo deserializaci v různé časy. Následující tabulka vysvětluje, kdy použít každý atribut.  
  
|Atribut|Pokud odpovídající metoda je volána|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Volá se před serializace typu.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Volá se po serializace typu.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Volá se před deserializaci typu.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Volá se po deserializaci typu.|  
  
 Metody musí přijmout <xref:System.Runtime.Serialization.StreamingContext> parametr.  
  
 Tyto metody jsou primárně určený pro použití se službou Správa verzí nebo inicializace. Během deserializace se nazývají žádné konstruktory. Proto datové členy není možné správně inicializovat (pro určený výchozí hodnoty) Pokud data pro tyto členy chybí v příchozím datovém proudu, například pokud data pocházejí z předchozí verze typ, který chybí některé datové členy. Chcete-li vyřešit tento problém, použijte metoda zpětného volání, které jsou označené jako <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak je znázorněno v následujícím příkladu.  
  
 Můžete označit pouze jednu metodu podle typu k jednotlivým atributům předchozí zpětného volání.  
  
### <a name="example"></a>Příklad  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [Verze serializace](../../../../docs/standard/serialization/version-tolerant-serialization.md)
