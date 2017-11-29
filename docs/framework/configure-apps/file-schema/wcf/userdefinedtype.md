---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0baac8dc6a9899261a490a257dbae0e7eb4d2ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserdefinedtypegt"></a>&lt;userDefinedType&gt;
Představuje uživatel definovaný typ (UDT), které má být součástí kontraktu služby.  
  
 \<systém. ServiceModel >  
\<comContracts >  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
         </userDefinedType>  
      </userDefinedTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`name`|Volitelný atribut, který obsahuje řetězec, který obsahuje název typu čitelné. Tento není používán modulu runtime ale pomáhá čtečka čipových karet k rozlišení typy.|  
|`TypeDefID`|Identifikátor GUID řetězec, který určuje konkrétní typ UDT v knihovně registrovaného typu.|  
|`TypeLibID`|Identifikátor GUID řetězec, který identifikuje registrovaného typu knihovnu, která definuje typ.|  
|`TypeLibVersion`|Řetězec, který určuje typ knihovní verze, která definuje typ.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekce `userDefinedType` elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Modul runtime integrace COM + vytvoří služby zkontrolováním knihovny typů. Pokud komponentu modelu COM + obsahuje metody, které předat hodnotu typu VARIANT, systém nemůže určit skutečné typy, které mají být předána před runtime. Proto při pokusu o předání uživatel definovaný typ (UDT) v rámci hodnotu typu VARIANT se nezdaří, protože není známý typ pro serializaci.  
  
 Chcete-li tento problém obejít, můžete přidat UDT do konfiguračního souboru tak, aby mohly být zahrnuta jako známé typy na příslušnou službu kontrakt. Chcete-li to provést, máte k jednoznačné identifikaci UDT a smluv, tedy původní COM alespoň jedno rozhraní používající ho.  
  
 Následující příklad ukazuje dva konkrétní UDT k přidání <`userDefinedTypes`> oddílu konfiguračního souboru pro tento účel.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
      namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"  
      name="_Broker"  
      requireSession="true">  
      <userDefinedTypes>  
         <userDefinedType name="CustomerType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">  
         </userDefinedType>  
         <userDefinedType name="AddressType"  
            typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"  
            typeLibVersion="1.0"  
            typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">  
         </userDefinedType>  
      </userDefinedTypes>  
      <exposedMethods>  
         <exposedMethod name="BuyStock" />  
         <exposedMethod name="SellStock" />  
         <exposedMethod name="ExecuteTransaction" />  
      </exposedMethods>  
  </comContract>  
</comContracts>  
```  
  
 Při inicializaci služby runtime integrace vyhledá určené typy a přidá je do kolekce známé typy pro zadaný smlouvy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [Integrace s aplikacemi modelu COM +](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Postupy: Konfigurace nastavení služby COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
