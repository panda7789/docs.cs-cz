---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2734060c855b59e5ff47ae674862dc57b7ddb5e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270764"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> Element
Určuje, zda je výchozí chování, které je umožnit hostitelský modul runtime pro přepsání nastavení konfigurace pro doménu aplikace, zakázáno.  
  
 \<Konfigurace > – Element  
\<modul runtime > – Element  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Povoleno|Požadovaný atribut.<br /><br /> Určuje, zda je výchozí možnost přepsat nastavení Fusion zakázaný.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Nezakazujte přepsat nastavení Fusion. Jedná se o výchozí chování, počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Zakážete možnost přepsat nastavení Fusion. To obnoví na chování starších verzích rozhraní .NET Framework.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], výchozí chování je umožnit <xref:System.AppDomainManager> určeného k přepsání nastavení konfigurace s použitím <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodu <xref:System.AppDomainSetup> objekt, který je předán vaší implementace nástroje <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metodu do vaší podtřídy aplikace <xref:System.AppDomainManager>. Pro výchozí domény aplikace přepíší nastavení, které můžete změnit nastavení zadané v konfiguračním souboru aplikace. Pro další aplikační domény, mohou přepsat nastavení konfigurace, které bylo předáno <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody.  
  
 Můžete předat nové informace o konfiguraci, nebo předat hodnotu null (`Nothing` v jazyce Visual Basic) Chcete-li odstranit informace o konfiguraci, která byla předána.  
  
 Nepředávejte informace o konfiguraci pro obě <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost a <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda. Pokud předáte informace o konfiguraci na obě, informace můžete předat <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost se ignoruje, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepíše informace o konfiguraci z konfiguračního souboru aplikace. Pokud používáte <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastností, můžete předat hodnotu null (`Nothing` v jazyce Visual Basic) na <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody, chcete-li odstranit všechny konfigurace bajtů, které byly zadány při volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> – metoda.  
  
 Kromě informací o konfiguraci, můžete změnit následující nastavení na <xref:System.AppDomainSetup> objekt, který je předán implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, a <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Jako alternativu k použití `<disableFusionUpdatesFromADManager>` element, můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí. V registru, vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` pod `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1. Na příkazovém řádku, nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na hodnotu 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat pomocí přepsání nastavení Fusion `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:
- [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
