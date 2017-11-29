---
title: "&lt;Usesmallinternalthreadstacks –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a>&lt;Usesmallinternalthreadstacks –&gt; – Element
Požadavky, modul CLR (CLR) snížit velikost paměti, použijte zadáním velikosti explicitní zásobníku při vytváření určitých vláken, která se používá interně, místo použití výchozí velikost zásobníku pro tyto vlákna.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<Usesmallinternalthreadstacks – > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, zda požadavek, aby velikosti CLR použijte explicitní zásobníku místo výchozí velikost zásobníku při vytváření určitých vláken, která se používá interně. Explicitní zásobníku velikosti jsou menší než výchozí velikost zásobníku 1 MB.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|true|Požádat o velikosti explicitní zásobníku.|  
|false|Použijte výchozí velikost zásobníku. Toto je výchozí nastavení pro [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element konfigurace slouží k vyžádání použití snížené virtuální paměti v procesu, protože velikosti explicitní vlákno, které modulu CLR používá pro interní podprocesů, pokud je dodržení požadavku, jsou menší než výchozí velikost.  
  
> [!IMPORTANT]
>  Tento element konfigurace je požadavek na modulu CLR, nikoli absolutní požadavek. V [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], žádost je dodržení pouze pro x86 architektura. Tento element může ignorován zcela v budoucích verzích modulu CLR nebo nahrazena explicitní zásobníku velikosti, které se vždycky použijí pro vybrané interní vlákna.  
  
 Určení, že tento element konfigurace obchoduje spolehlivost pro menší využití virtuální paměti Pokud modulu CLR ctí požadavek, protože menší velikost zásobníku může potenciálně zásobníku přesahuje více pravděpodobně.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak požádat o explicitní zásobníku použití CLR velikosti pro konkrétní vláken, která se používá interně.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
