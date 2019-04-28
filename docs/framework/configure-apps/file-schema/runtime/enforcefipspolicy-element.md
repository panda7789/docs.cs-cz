---
title: Element <enforceFIPSPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704960"
---
# <a name="enforcefipspolicy-element"></a>\<enforcefipspolicy – > – Element
Určuje, jestli chcete vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu se informace o zpracování normy FIPS (Federal).  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<enforcefipspolicy – > – Element  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, jestli se má povolit vynucení požadavek konfigurace počítače, musí být kryptografické algoritmy kompatibilní se standardem FIPS.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Value|Popis|  
|-----------|-----------------|  
|`true`|V případě, že váš počítač je nakonfigurován tak, aby vyžadovala kryptografické algoritmy pro rozpoznávání kompatibilní se standardem FIPS, tento požadavek se nevynutí. Pokud třída implementuje algoritmus, který není kompatibilní se standardem FIPS, konstruktory nebo `Create` metody pro danou třídu vyvolat výjimky při jejich spuštění na tomto počítači. Toto nastavení je výchozí.|  
|`false`|Kryptografické algoritmy, které používají aplikace nejsou musí být v souladu se standardem FIPS, bez ohledu na konfigurace počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 2.0, vytváření třídy, které implementují kryptografické algoritmy řídí konfiguraci počítače. Pokud je počítač nakonfigurovaný tak, aby vyžadovala algoritmy být v souladu se standardem FIPS, a třída implementuje algoritmus, který není kompatibilní se standardem FIPS, jakýkoliv pokus o vytvoření instance této třídy vyvolá výjimku. Vyvolat konstruktory <xref:System.InvalidOperationException> výjimky, a `Create` vyvolání metody <xref:System.Reflection.TargetInvocationException> výjimka s vnitřní <xref:System.InvalidOperationException> výjimky.  
  
 Pokud vaše aplikace funguje na počítačích, jejichž konfigurací vyžadovat dodržování standardu FIPS a vaše aplikace používá algoritmus, který není kompatibilní se standardem FIPS, aby se zabránilo common language runtime (CLR) z můžete tento prvek v konfiguračním souboru vynucování kompatibilita se standardem FIPS. Tento prvek byla zavedena v [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zabránit CLR vynucování kompatibilita se standardem FIPS.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Kryptografický model](../../../../../docs/standard/security/cryptography-model.md)
