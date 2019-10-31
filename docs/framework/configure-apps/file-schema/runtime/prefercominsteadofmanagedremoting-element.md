---
title: Element <PreferComInsteadOfManagedRemoting>
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
ms.openlocfilehash: 47c568a8d6e89a195414552b3db5953ee61d1e55
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116019"
---
# <a name="prefercominsteadofmanagedremoting-element"></a>\<element > PreferComInsteadOfManagedRemoting
Určuje, zda modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace pro všechna volání napříč hranicemi domény aplikace.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<PreferComInsteadOfManagedRemoting >**  
  
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
 Při nastavení atributu `enabled` na `true`se modul runtime chová takto:  
  
- Modul runtime nevolá [IUnknown:: QueryInterface](https://go.microsoft.com/fwlink/?LinkID=144867) pro rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) , když rozhraní [IUnknown](https://go.microsoft.com/fwlink/?LinkId=148003) vstoupí do domény prostřednictvím rozhraní modelu COM. Místo toho vytvoří obálku webRCW ( [za běhu](../../../../standard/native-interop/runtime-callable-wrapper.md) ) kolem objektu.  
  
- Modul runtime vrátí E_NOINTERFACE, když přijme `QueryInterface` volání pro rozhraní [IManagedObject](../../../unmanaged-api/hosting/imanagedobject-interface.md) pro libovolný [obálku](../../../../standard/native-interop/com-callable-wrapper.md) (doleva) typu com, která byla vytvořena v této doméně.  
  
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

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
