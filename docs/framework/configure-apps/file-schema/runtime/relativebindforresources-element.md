---
title: Element <relativeBindForResources>
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
ms.openlocfilehash: cd49d424019a4e8422fee0ae16217d49cfc456b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153903"
---
# <a name="relativebindforresources-element"></a>\<relativeBindForResources> Element
Optimalizuje sondu pro satelitní sestavení.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)\
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
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda běžný jazyk runtime optimalizuje sondu pro satelitní sestavení.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Doba běhu neoptimalizuje sondu pro satelitní sestavení. Toto je výchozí hodnota.|  
|`true`|Za běhu optimalizuje sondu pro satelitní sestavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 Správce prostředků obecně sonduje prostředky, jak je popsáno v tématu [Balení a nasazení prostředků.](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md) To znamená, že když Resource Manager sonduje pro konkrétní lokalizovanou verzi prostředku, může se podívat do globální mezipaměti sestavení, podívat se do složky specifické pro jazykovou verzi v základu kódu aplikace, dotazovat se Instalační služby systému Windows pro satelitní sestavení a vyvolat <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost. Prvek `<relativeBindForResources>` optimalizuje způsob, jakým Resource Manager sondy pro satelitní sestavení. Může zlepšit výkon při zjišťování zdrojů za následujících podmínek:  
  
- Při satelitní sestavení je nasazen ve stejném umístění jako sestavení kódu. Jinými slovy, pokud je sestavení kódu nainstalováno v globální mezipaměti sestavení, musí být zde nainstalována také satelitní sestavení. Pokud je sestavení kódu nainstalováno v základu kódu aplikace, satelitní sestavení musí být také nainstalována ve složce specifické pro jazykovou verzi v základu kódu.  
  
- Pokud instalační služba systému Windows není použita nebo se používá pouze zřídka pro instalaci satelitních sestavení na vyžádání.  
  
- Pokud kód aplikace nezpracovává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.  
  
 Nastavení `enabled` atributu `<relativeBindForResources>` prvku `true` pro optimalizaci sondy Správce prostředků pro satelitní sestavení následujícím způsobem:  
  
- Používá umístění sestavení nadřazeného kódu ke sondování pro satelitní sestavení.  
  
- Nedotazuje se Instalační služba systému Windows na satelitní sestavení.  
  
- To nevyvolává <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> událost.  
  
## <a name="see-also"></a>Viz také

- [Zabalení a nasazení prostředků](../../../resources/packaging-and-deploying-resources-in-desktop-apps.md)
- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
