---
title: '&lt;Parametr&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9db1921e2a6ee1ae2780f744c45fdb25efbf797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltparametergt"></a>&lt;Parametr&gt;
Určuje obecný parametr, pokud deklarovaný typ obecného typu.  
  
 \<System.Runtime.Serialization >  
\<dataContractSerializer >  
\<declaredTypes > elementu  
\<Přidat > elementu pro \<declaredTypes >  
\<Třída knownType > elementu  
\<parametr > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|index|Pokud je deklarovaný typ obecného typu, určuje obecný parametr, který vrátí typ známé.|  
|– typ|Řetězec, který popisuje známý typ použitý k serializaci a deserializaci.|  
  
## <a name="index-attribute"></a>index atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|"0"|První parametr obecného typu. Například <xref:System.Collections.Generic.List%601> má jenom jeden parametr. Pokud se používají jako deklarovaný typ indexu by nastavena na hodnotu "0".|  
|"1"|Druhý parametr obecného typu. Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry. Pokud je známý typ vrácené druhý parametr, nastavte atribut index "1".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Třída knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Určuje známému typu, který může být vrácen pouze pole nebo vlastnost deklarovaného typu.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]známé typy, najdete v části [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.  
  
 Tento element konfigurace nemůže mít oba atributy ve stejnou dobu. Pokud oba atributy jsou nastavené, <xref:System.Configuration.ConfigurationErrorsException> dojde.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
