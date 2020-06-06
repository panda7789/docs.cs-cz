---
title: Element <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153903"
---
# <a name="relativebindforresources-element"></a>Element \<relativeBindForResources>
Optimalizuje sondu pro satelitní sestavení.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<relativeBindForResources>**  
  
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul CLR (Common Language Runtime) optimalizuje test pro satelitní sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|`false`|Modul runtime neoptimalizuje sondu pro satelitní sestavení. Toto je výchozí hodnota.|  
|`true`|Modul runtime optimalizuje sondu pro satelitní sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Obecně Správce prostředků sondy pro prostředky, jak je popsáno v tématu [balení a nasazení prostředků](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) . To znamená, že když Správce prostředků sondy pro určitou lokalizovanou verzi prostředku, může to vypadat v globální mezipaměti sestavení (GAC), vyhledat složku specifickou pro jazykovou verzi v základu kódu aplikace, dotazovat Instalační služba systému Windows pro satelitní sestavení a vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost. `<relativeBindForResources>`Prvek optimalizuje způsob, jakým Správce prostředků sondy pro satelitní sestavení. Může zvýšit výkon při zjišťování prostředků za následujících podmínek:  
  
- Když satelitní sestavení je nasazeno ve stejném umístění jako sestavení kódu. Jinými slovy, pokud je sestavení kódu nainstalováno v globální mezipaměti sestavení (GAC), musí být také nainstalovaná satelitní sestavení. Pokud je sestavení kódu nainstalováno v základu kódu aplikace, musí být satelitní sestavení také nainstalována do složky specifické pro jazykovou verzi v základu kódu.  
  
- Pokud se Instalační služba systému Windows nepoužívá nebo se používá jenom zřídka pro instalaci satelitních sestavení na vyžádání.  
  
- Když kód aplikace událost nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .  
  
 Nastavení `enabled` atributu `<relativeBindForResources>` elementu pro `true` optimalizaci správce prostředků sondy pro satelitní sestavení následujícím způsobem:  
  
- Používá umístění sestavení nadřazeného kódu pro testování satelitního sestavení.  
  
- Nedotazuje se Instalační služba systému Windows pro satelitní sestavení.  
  
- Událost nevyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- [Zabalení a nasazení prostředků](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
