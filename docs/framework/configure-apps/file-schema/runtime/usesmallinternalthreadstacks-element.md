---
title: Element <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9833d768b84faaf6e1dcf8c9cb8b00b92adc3d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673983"
---
# <a name="usesmallinternalthreadstacks-element"></a>\<Usesmallinternalthreadstacks – > – Element
Požadavky, že modul CLR (CLR) snížit velikost paměti, používat tak, že zadáte zásobníku explicitní velikost při vytváření příslušná vlákna, které se používá interně, místo použití výchozí velikost zásobníku pro tato vlákna.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<Usesmallinternalthreadstacks – > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, zda požadavek, aby velikosti zásobníku explicitní použití CLR místo výchozí velikost zásobníku při vytváření příslušná vlákna, které se používá interně. Explicitní zásobníku velikosti jsou menší než výchozí velikost zásobníku 1 MB.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|true|Žádost o velikosti explicitní zásobníku.|  
|false|Použijte výchozí velikost zásobníku. Toto je výchozí nastavení pro [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace slouží k vyžádání použití nižší virtuální paměti v procesu, protože velikosti explicitní vlákno, které používá modul CLR pro interní podprocesů, pokud požadavek zachovaný, jsou menší než výchozí velikost.  
  
> [!IMPORTANT]
>  Tento prvek konfigurace je požadavek na modul CLR, nikoli nezbytný požadavek. V [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], požadavek zachovaný pouze pro x86 architektury. Tento element může být ignorovány zcela v budoucích verzích CLR nebo nahrazuje velikosti explicitní zásobníku, které se vždycky použijí pro interní vybraná vlákna.  
  
 Určení, že tento prvek konfigurace obchoduje spolehlivost pro menší využití virtuální paměti Pokud CLR respektuje požadavek, protože menší velikosti zásobníku může potenciálně zásobníku pravděpodobně přetečení.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak požádat o zásobníku explicitní použití CLR velikosti pro určité vlákna, která se používá interně.  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
