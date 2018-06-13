---
title: '&lt;disablefusionupdatesfromadmanager –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745887"
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a>&lt;disablefusionupdatesfromadmanager –&gt; – Element
Určuje, zda je výchozí chování, které je umožnit runtime hostitelů pro přepsání nastavení konfigurace pro doménu aplikace, zakázána.  
  
 \<Konfigurace > elementu  
\<modul runtime > elementu  
\<disablefusionupdatesfromadmanager – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|povoleno|Požadovaný atribut.<br /><br /> Určuje, zda je výchozí možnost pro přepsání nastavení Fusion zakázána.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0|Možnost pro přepsání nastavení Fusion nezakazujte. Toto je výchozí chování, počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].|  
|1|Zakažte možnost pro přepsání nastavení Fusion. To obnoví chování starší verze rozhraní .NET Framework.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], výchozí chování je umožnit <xref:System.AppDomainManager> objekt, který chcete přepsat nastavení konfigurace pomocí <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodu <xref:System.AppDomainSetup> objekt, který je předán do vaší implementace z <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda ve vašem podtřídou třídy <xref:System.AppDomainManager>. Pro výchozí doménu aplikace potlačí nastavení, která můžete změnit nastavení, která měla určeného konfiguračního souboru aplikace. Pro ostatní domény aplikace, se přepíší nastavení konfigurace, které byly předány <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metoda.  
  
 Můžete předat nové informace o konfiguraci, nebo zadejte hodnotu null (`Nothing` v jazyce Visual Basic) k odstranění informace o konfiguraci, která byla předána.  
  
 Nepředávejte informace o konfiguraci na obě <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost a <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda. Pokud předáte i informace o konfiguraci, informace můžete předat <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost je ignorována, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepsání informace o konfiguraci z konfiguračního souboru aplikace. Pokud použijete <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost, můžete předat hodnotu null (`Nothing` v jazyce Visual Basic) k <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda odstranit všechny konfigurace bajtů, které byly zadány ve volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metoda.  
  
 Kromě informací o konfiguraci, můžete změnit na následující nastavení <xref:System.AppDomainSetup> objekt, který je předán do vaší implementace nástroje <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metoda: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, a <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu, můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí. V registru, vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` pod `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1. Na příkazovém řádku, nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat možnost pro přepsání nastavení Fusion pomocí `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
