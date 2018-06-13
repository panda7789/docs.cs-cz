---
title: '&lt;Prefercominsteadofmanagedremoting –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- <PreferComInsteadOfManagedRemoting> element
- PreferComInsteadOfManagedRemoting element
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cac4ebb46fabad49e2e4e6a7d566522ca027094
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745471"
---
# <a name="ltprefercominsteadofmanagedremotinggt-element"></a>&lt;Prefercominsteadofmanagedremoting –&gt; – Element
Určuje, zda modul runtime bude používat zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci pro všechna volání napříč hranicemi domény aplikace.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Prefercominsteadofmanagedremoting – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Znamená, zda modul runtime použije zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci napříč hranicemi domény aplikace.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime použije vzdálenou komunikaci napříč hranicemi domény aplikace. Toto nastavení je výchozí.|  
|`true`|Modul runtime použije zprostředkovatel komunikace s objekty COM napříč hranicemi domény aplikace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Když nastavíte `enabled` atribut `true`, modul runtime chová následovně:  
  
-   Modul runtime nevyvolá [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní, kdy [IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003) rozhraní zadá domény prostřednictvím rozhraní modelu COM. Místo toho vytvoří [obálka volatelná za běhu](../../../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) kolem objektu.  
  
-   Modul runtime vrátí E_NOINTERFACE při přijetí `QueryInterface` volání pro [IManagedObject](../../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md) rozhraní pro všechny [obálka volatelná aplikacemi COM](../../../../../docs/framework/interop/com-callable-wrapper.md) (doleva), byl vytvořen v této doméně.  
  
 Tyto dvě chování Ujistěte se, že všechna volání přes COM rozhraní mezi spravovaných objektů mezi použijte hranice domény aplikace modelu COM a zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak určit, že modul runtime by měl používat COM spolupráce napříč hranicemi izolace:  
  
```xml  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
