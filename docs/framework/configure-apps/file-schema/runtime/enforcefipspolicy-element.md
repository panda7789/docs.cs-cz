---
title: "&lt;enforcefipspolicy –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd593c17d752b35919985aad37f675c62e6ce34
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforcefipspolicy –&gt; – Element
Určuje, jestli vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu s na zpracování standardů FIPS (Federal Information).  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<enforcefipspolicy – > elementu  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, jestli se má povolit vynucení požadavek konfigurace počítače, musí být kryptografické algoritmy kompatibilní s FIPS.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`true`|Pokud váš počítač je nakonfigurován tak, aby vyžadovala kryptografické algoritmy být kompatibilní se standardem FIPS, že požadavek je vyžadována. Pokud třída implementuje algoritmu, který není kompatibilní s FIPS, konstruktorů nebo `Create` metody pro tuto třídu generování výjimek, pokud jsou v tomto počítači spustit. Toto nastavení je výchozí.|  
|`false`|Kryptografické algoritmy, které používají aplikace nejsou nemusí být kompatibilní s FIPS, bez ohledu na konfigurace počítače.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Od verze rozhraní .NET Framework 2.0, řídí vytváření třídy, které implementují kryptografické algoritmy konfiguraci počítače. Pokud je počítač nakonfigurovaný tak, aby vyžadovala algoritmy s cílem být v souladu se standardem FIPS, a třída implementuje algoritmu, který není kompatibilní s FIPS, pokusy o vytvoření instance této třídy vyvolá výjimku. Konstruktory throw <xref:System.InvalidOperationException> výjimka, a `Create` metody throw <xref:System.Reflection.TargetInvocationException> výjimka vnitřní <xref:System.InvalidOperationException> výjimka.  
  
 Pokud vaše aplikace běží na počítačích, jejichž konfigurace vyžadují kompatibilitu se standardem FIPS, a vaše aplikace používá algoritmus, který není kompatibilní s FIPS, aby se zabránilo common language runtime (CLR) z můžete tento element v konfiguračním souboru vynucování soulad se standardem FIPS. Tento element byla zavedena v [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zabránit vynucovat soulad se standardem FIPS modulu CLR.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Kryptografický Model](../../../../../docs/standard/security/cryptography-model.md)
