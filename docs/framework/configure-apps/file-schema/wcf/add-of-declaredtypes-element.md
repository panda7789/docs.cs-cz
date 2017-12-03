---
title: '&lt;add&gt; elementu &lt;declaredTypes&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71f9c2b45f631eb2d9021254d2866f0092ebb079
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a>&lt;add&gt; elementu &lt;declaredTypes&gt;
Přidá typ používaný <xref:System.Runtime.Serialization.DataContractSerializer> během deserializace. Každý deklarovaný typ obsahuje známé typy, které bude vrácen jako pole nebo vlastnost deklarovaného typu.  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
\<Přidat > z \<declaredTypes >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|– typ|Požadovaný atribut typu string.<br /><br /> Určuje název typu (včetně oboru názvů), název sestavení, číslo verze, jazykové verze a tokenu veřejného klíče.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Třída knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Určuje známý typ deklarovaný typ, který je přidáván. Pokud deklarovaný typ je obecný typ, pak musíte taky přidat parametr element na `<knownType>` elementu, který chcete určit, které obecný parametr se používá k vrácení známý typ.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|Obsahuje typy, které vyžadují známé typy během deserializace pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Poznámky  
 Další informace o známé typy najdete v tématu [známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) a <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Najdete v článku [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) příklad použití tohoto elementu.  
  
> [!NOTE]
>  Pokud přidáte <xref:System.Object> zadejte jako `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> je vyvolána výjimka. Důvodem je, že <xref:System.Object> typu nelze použít jako deklarovaný typ v konfiguraci.  
  
## <a name="example"></a>Příklad  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Známé typy kontraktů dat](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<Přidat > z \<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
