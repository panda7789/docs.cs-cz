---
title: '&lt;relativebindforresources –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ae5d1ca6403d84c9828dcf9550e9fbf40b28e1b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativebindforresources –&gt; – Element
Tato kontrola se optimalizuje pro satelitní sestavení.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<relativebindforresources – > elementu  
  
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
|`false`|Modul runtime není optimální sondy pro satelitní sestavení. Jedná se o výchozí hodnotu.|  
|`true`|Modul runtime optimalizuje sondy pro satelitní sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně platí, Resource Manager sondy pro prostředky, jak je uvedeno v [balení a nasazení prostředků](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) tématu. To znamená, že když Resource Manager sondy pro konkrétní lokalizované verze prostředku, může hledat v globální mezipaměti sestavení, ve složce specifické pro jazykovou verzi v základní, dotazu kód aplikace Instalační služby systému Windows vyhledejte satelitní sestavení a zvýšit <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí. `<relativeBindForResources>` Element optimalizuje způsob, ve kterém se správce prostředků sondy pro satelitní sestavení. Se může zlepšit výkon při zjišťování prostředků za následujících podmínek:  
  
-   Satelitní sestavení je při nasazení ve stejném umístění jako sestavení kódu. Jinými slovy Pokud kód sestavení je nainstalována v globální mezipaměti sestavení, satelitní sestavení musí být nainstalována také existuje. Pokud je kód sestavení nainstalováno v kódu aplikace základní, satelitní sestavení musí být také nainstalovaný ve složce specifické pro jazykovou verzi v základu kódu.  
  
-   Když instalační služba systému Windows nepoužívá nebo jen zřídka se používá pro instalaci na vyžádání satelitních sestavení.  
  
-   Pokud kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
 Nastavení `enabled` atribut `<relativeBindForResources>` element `true` optimalizuje Resource Manager testu pro satelitní sestavení následujícím způsobem:  
  
-   Umístění nadřazeného kódu sestavení na základě testu pro satelitní sestavení.  
  
-   Neprohledává Instalační služby systému Windows pro satelitní sestavení.  
  
-   Nelze vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událostí.  
  
## <a name="see-also"></a>Viz také  
 [Zabalení a nasazení prostředků](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
