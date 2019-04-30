---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 46beb88cedf051ed1683161b6ed9b37273ed01f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769834"
---
# <a name="userdefinedtype"></a>\<typu userDefinedType >
Představuje uživatele definované typ (UDT), který je součástí kontraktu služby.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
\<userDefinedTypes >  
  
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
|`name`|Volitelný atribut, který obsahuje řetězec, který poskytuje název čitelného typu. To se nepoužije, modul runtime ale pomáhá čtečku k rozlišení typů.|  
|`TypeDefID`|Řetězec identifikátoru GUID identifikující konkrétní uživatelem Definovaný typ v rámci knihovny registrovaných typů.|  
|`TypeLibID`|Řetězec identifikátoru GUID identifikující knihovnu registrovaných typů, která definuje typ.|  
|`TypeLibVersion`|Řetězec, který určuje verzi knihovny typů, která definuje typ.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`userDefinedTypes`|Kolekce `userDefinedType` elementy.|  
  
## <a name="remarks"></a>Poznámky  
 Modul runtime integrace modelu COM + vytvoří služby zkontrolováním knihovny typů. Když komponenta modelu COM + obsahuje metody, které předat hodnotu typu VARIANT, systém nemůže určit skutečné typy, které mají být předány před modulu runtime. Proto se při pokusu o předání uživatel definovaný typ (UDT) v rámci hodnotu typu VARIANT, nezdaří se, protože není známý typ pro serializaci.  
  
 Chcete-li tento problém obejít, můžete přidat uživatelsky definované typy do konfiguračního souboru tak, aby mohly být zahrnuty jako známé typy kontraktu příslušnou službu. Aby bylo možné učinit, máte k jednoznačné identifikaci UDT a kontrakty, to znamená, původní COM rozhraní, která ji používá.  
  
 Následující příklad ukazuje dva konkrétní uživatelsky definovaný typ pro přidání <`userDefinedTypes`> oddílu konfiguračního souboru pro tento účel.  
  
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
  
 Při inicializaci služby vyhledá určené typy prostředí integration runtime a přidá je do kolekce známých typů pro zadaný smlouvy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Integrace s aplikacemi modelu COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Postupy: Konfigurace nastavení služby modelu COM +](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
