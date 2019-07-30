---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c7a558af17493c955b4f148d0abf7f42c9dd6f8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629432"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<PreferComInsteadOfManagedRemoting> Element
Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.  
  
 \<> Konfigurace  
\<> modulu runtime  
\<PreferComInsteadOfManagedRemoting>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime bude používat vzdálenou komunikaci napříč hranicemi aplikační domény. Toto nastavení je výchozí.|  
|`true`|Modul runtime bude používat zprostředkovatele komunikace s objekty COM napříč hranicemi aplikační domény.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Při nastavení `enabled` atributu na `true`se modul runtime chová takto:  
  
- Modul runtime nevolá [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pro rozhraní [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) , když rozhraní [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) vstoupí do domény prostřednictvím rozhraní modelu COM. Místo toho vytvoří obálku webRCW ( [za běhu](../../../../../docs/standard/native-interop/runtime-callable-wrapper.md) ) kolem objektu.  
  
- Modul runtime vrátí E_NOINTERFACE, když přijme `QueryInterface` volání rozhraní [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) pro libovolný obálku s voláním [modelu COM](../../../../../docs/standard/native-interop/com-callable-wrapper.md) (doleva), která byla vytvořena v této doméně.  
  
 Tato dvě chování zajišťují, že všechna volání rozhraní COM mezi spravovanými objekty napříč hranicemi aplikační domény používají místo vzdálené komunikace COM a COM Interop.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že modul runtime má používat zprostředkovatele komunikace s objekty COM přes hranice izolace:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
