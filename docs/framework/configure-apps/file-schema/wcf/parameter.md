---
title: '&lt;Parametr&gt;'
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: 82a2f5c46c698508695fe5f13f67059860a50713
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148289"
---
# <a name="ltparametergt"></a>&lt;Parametr&gt;
Určuje obecný parametr, je-li deklarovaný typ obecného typu.  
  
 \<System.Runtime.Serialization >  
\<dataContractSerializer >  
\<declaredTypes > – Element  
\<Přidat > – element pro \<declaredTypes >  
\<Třída knownType > – Element  
\<parametr > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<parameter index="Integer"
           type="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|index|Když je deklarovaný typ obecného typu, určuje obecný parametr, který vrací známý typ.|  
|– typ|Řetězec, který popisuje známý typ používaný k serializaci a deserializaci.|  
  
## <a name="index-attribute"></a>Atribut indexu  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|"0"|První parametr v obecném typu. Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr. Pokud se používá jako deklarovaný typ, index se nastavuje na hodnotu "0".|  
|"1"|Druhý parametr obecného typu. Například <xref:System.Collections.Generic.Dictionary%602> má dva parametry. Pokud známý typ není vrácena druhým parametrem, nastavte atribut indexu na hodnotu "1".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Třída knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Určuje známý typ, který může být vrácen pole nebo vlastnost deklarovaného typu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známých typů najdete v tématu [známé typy kontraktů dat.](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Zobrazit [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto prvku.  
  
 Tento prvek konfigurace nemůže mít oba atributy ve stejnou dobu. Pokud jsou oba atributy nastavené, <xref:System.Configuration.ConfigurationErrorsException> vyvolá.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
