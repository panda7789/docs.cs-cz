---
title: <parameter>
ms.date: 03/30/2017
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
ms.openlocfilehash: c3f2179835ad1232e115cad0decdd3d41bbdc160
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932838"
---
# <a name="parameter"></a>\<> parametru
Určuje obecný parametr, je-li deklarovaný typ obecný typ.  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
\<declaredTypes – element >  
\<Přidat > element pro \<> declaredTypes  
\<Třída KnownType – element >  
\<parametr > element  
  
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
|index|Když deklarovaný typ je obecný typ, určuje obecný parametr, který vrátí známý typ.|  
|– typ|Řetězec, který popisuje známý typ používaný pro serializaci a deserializaci.|  
  
## <a name="index-attribute"></a>index – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|"0"|První parametr v obecném typu. Například <xref:System.Collections.Generic.List%601> má pouze jeden parametr. Pokud je použit jako deklarovaný typ, index by byl nastaven na hodnotu "0".|  
|"1"|Druhý parametr v obecném typu. Například a <xref:System.Collections.Generic.Dictionary%602> má dva parametry. Pokud je známý typ vrácen druhým parametrem, nastavte atribut index na hodnotu "1".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|Určuje známý typ, který může být vrácen polem nebo vlastností deklarovaného typu.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známých typech naleznete v tématu [známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Příklad použití tohoto prvku naleznete v [ \<> DataContractSerializer](datacontractserializer-element.md) .  
  
 Tento prvek konfigurace nemůže obsahovat oba atributy současně. Pokud jsou nastaveny oba atributy, <xref:System.Configuration.ConfigurationErrorsException> dojde k.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Známé typy kontraktů dat](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<add>](add-of-declaredtypes-element.md)
