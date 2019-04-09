---
title: <NetFx40_LegacySecurityPolicy> Element
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a0ca8560fcd5d7f9d171df3e3b4c3f42e78641
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075987"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy> Element
Určuje, zda modul runtime používá starší verzi kódu zásady zabezpečení přístupu (CAS).  
  
 \<Konfigurace >  
\<modul runtime >  
<NetFx40_LegacySecurityPolicy>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, zda modul runtime používá starší zásadu CAS.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Modul runtime nepoužívá starší zásadu CAS. Toto nastavení je výchozí.|  
|`true`|Modul runtime používá starší zásadu CAS.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o možnostech inicializace modulu runtime.|  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 3.5 a starší verze zásad CAS je vždy v vliv. V [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], musí být povolené zásady CAS.  
  
 Zásady CAS je specifické pro verzi. Vlastní zásady CAS, které existují v dřívějších verzích rozhraní .NET Framework musí být zadány znovu v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 Použití `<NetFx40_LegacySecurityPolicy>` elementu [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] sestavení nemá vliv na [kód transparentní pro zabezpečení](../../../../../docs/framework/misc/security-transparent-code.md); stále platí pravidla transparentnosti.  
  
> [!IMPORTANT]
>  Použití `<NetFx40_LegacySecurityPolicy>` element může způsobit snížení výkonu pro sestavení nativních bitových kopií, které jsou vytvořené [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) , která nejsou v nainstalovaná [globální mezipaměti sestavení ](../../../../../docs/framework/app-domains/gac.md). Snížení výkonu způsobuje nemožnost modul runtime k načtení sestavení jako nativní bitové kopie, když se atribut používá, což vede k jejich načtených sestavení jako just-in-time.  
  
> [!NOTE]
>  Pokud zadáte cílovou verzi rozhraní .NET Framework, která je starší než [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] v nastavení projektu pro projekt sady Visual Studio, zásady CAS bude povolena, včetně všechny vlastní zásady CAS zadané pro tuto verzi. Ale nebudete moci používat nové [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] typy a členy. Starší verzi rozhraní .NET Framework můžete také zadat pomocí [ \<supportedRuntime > element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) v schéma nastavení spouštění ve vaší [konfiguračního souboru aplikace](../../../../../docs/framework/configure-apps/index.md).  
  
> [!NOTE]
>  Syntaxe konfigurační soubor je velká a malá písmena. Jak je uvedeno v části Syntaxe a příkladu, měli byste použít syntaxi.  
  
## <a name="configuration-file"></a>Konfigurační soubor  
 Tento element lze použít pouze v konfiguračním souboru aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolte starší zásadu CAS pro aplikaci.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
