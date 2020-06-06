---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854843"
---
# \<userDefinedType>
Představuje uživatelem definovaný typ (UDT), který má být zahrnut do kontraktu služby.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
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
|`name`|Volitelný atribut, který obsahuje řetězec, který poskytuje název čitelného typu. Toto není používáno modulem runtime, ale pomáhá čtenářům odlišit typy.|  
|`TypeDefID`|Řetězec identifikátoru GUID, který identifikuje konkrétní typ UDT v registrované knihovně typů.|  
|`TypeLibID`|Řetězec identifikátoru GUID identifikující knihovnu registrovaných typů, která definuje typ.|  
|`TypeLibVersion`|Řetězec, který určuje verzi knihovny typů, která definuje typ.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekce `userDefinedType` prvků.|  
  
## <a name="remarks"></a>Poznámky  
 Prostředí Integration runtime modelu COM+ vytvoří služby kontrolou knihovny typů. Pokud komponenta modelu COM+ obsahuje metody, které předávají VARIANTu, systém nemůže určit skutečné typy, které mají být předány před modulem runtime. Proto při pokusu o předání uživatelem definovaného typu (UDT) v rámci varianty se nezdaří, protože se nejedná o známý typ pro serializaci.  
  
 Chcete-li tento problém obejít, můžete přidat UDT do konfiguračního souboru, aby je bylo možné zahrnout do příslušného kontraktu služby jako známé typy. Aby to bylo možné, musíte jedinečně identifikovat UDT a kontrakty, tedy původní rozhraní COM, která je používá.  
  
 Následující příklad ukazuje přidání dvou specifických UDT do `userDefinedTypes` oddílu <> konfiguračního souboru pro tento účel.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
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
  
 Při inicializaci služby modul Integration runtime vyhledá zadané typy a přidá je do kolekce známých typů pro zadané kontrakty.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [Integrace s aplikacemi modelu COM+](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Postupy: Konfigurace nastavení služby modelu COM+](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
