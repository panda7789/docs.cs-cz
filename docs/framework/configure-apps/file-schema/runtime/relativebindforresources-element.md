---
title: '&lt;relativebindforresources –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1933fad8ea87351a56fcc7dd4a4fd67e890b58f5
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613892"
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativebindforresources –&gt; – Element
Optimalizuje sondy pro satelitní sestavení.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<relativebindforresources – > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul common language runtime optimalizuje sondy pro satelitní sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime neoptimalizuje sondy pro satelitní sestavení. Jedná se o výchozí hodnotu.|  
|`true`|Modul runtime optimalizuje sondy pro satelitní sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, sondy Resource Manageru pro prostředky, jak je uvedeno v [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tématu. To znamená, že pokud pro konkrétní lokalizovanou verzi prostředkem sondy Resource Manageru, může hledat v globální mezipaměti sestavení, podívejte se do složky specifické pro jazykovou verzi na základní, dotaz kód aplikace Instalační služby systému Windows pro satelitní sestavení a zvýšit <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> události. `<relativeBindForResources>` Element optimalizuje způsob, ve kterém testy Resource Manageru pro satelitní sestavení. To může zlepšit výkon při zjišťování prostředků za následujících podmínek:  
  
-   Satelitní sestavení je při nasazení ve stejném umístění jako sestavení kódu. Jinými slovy Pokud sestavení kódu je nainstalováno v globální mezipaměti sestavení, satelitní sestavení musí být nainstalována také existuje. Pokud je kód sestavení nainstalovaná v základu kódu vaší aplikace, musí satelitní sestavení nainstalována také do složky specifické pro jazykovou verzi v základu kódu.  
  
-   Když instalační služby systému Windows se nepoužívá nebo jen zřídka se používá pro instalaci na vyžádání satelitních sestavení.  
  
-   Pokud kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
 Nastavení `enabled` atribut `<relativeBindForResources>` elementu `true` optimalizuje test Resource Manageru pro satelitní sestavení následujícím způsobem:  
  
-   Umístění sestavení kódu nadřazené používá pro sběr dat pro satelitní sestavení.  
  
-   Neprohledává Instalační služby systému Windows pro satelitní sestavení.  
  
-   Nevyvolával <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
## <a name="see-also"></a>Viz také  
- [Zabalení a nasazení prostředků](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
