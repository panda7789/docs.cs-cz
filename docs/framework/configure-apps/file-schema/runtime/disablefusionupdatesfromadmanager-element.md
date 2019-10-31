---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117447"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<element > disableFusionUpdatesFromADManager
Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|umožněn|Požadovaný atribut.<br /><br /> Určuje, jestli je zakázaná výchozí možnost přepsat nastavení fúze.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|0,8|Nepovolujte možnost přepsat nastavení fúze. Toto je výchozí chování, počínaje .NET Framework 4.|  
|první|Zakáže možnost přepsat nastavení fúze. Tím se vrátí chování dřívějších verzí .NET Framework.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 je výchozím chováním umožnit objektu <xref:System.AppDomainManager> přepsat nastavení konfigurace pomocí vlastnosti <xref:System.AppDomainSetup.ConfigurationFile%2A> nebo metody <xref:System.AppDomainSetup.SetConfigurationBytes%2A> objektu <xref:System.AppDomainSetup>, který se předává implementaci metody <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>. , v podtřídě <xref:System.AppDomainManager>. U výchozí domény aplikace nastavení, které změníte, přepíše nastavení, která byla určena konfiguračním souborem aplikace. U ostatních aplikačních domén přepíše nastavení konfigurace, která byla předána metodě <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 Můžete buď předat nové konfigurační informace, nebo předat hodnotu null (`Nothing` v Visual Basic), aby se vyloučily informace o konfiguraci, které byly předány.  
  
 Nedávejte informace o konfiguraci do vlastnosti <xref:System.AppDomainSetup.ConfigurationFile%2A> a do metody <xref:System.AppDomainSetup.SetConfigurationBytes%2A>. Pokud předáte informace o konfiguraci do obou, informace, které předáte do vlastnosti <xref:System.AppDomainSetup.ConfigurationFile%2A>, budou ignorovány, protože metoda <xref:System.AppDomainSetup.SetConfigurationBytes%2A> Přepisuje informace o konfiguraci z konfiguračního souboru aplikace. Použijete-li vlastnost <xref:System.AppDomainSetup.ConfigurationFile%2A>, můžete metodě <xref:System.AppDomainSetup.SetConfigurationBytes%2A> předat hodnotu null (`Nothing` v Visual Basic) a odstranit tak všechny konfigurační bajty, které byly zadány ve volání metody <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> nebo <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>.  
  
 Kromě informací o konfiguraci můžete změnit následující nastavení objektu <xref:System.AppDomainSetup>, který se předává implementaci metody <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>a <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.  
  
 Jako alternativu k použití prvku `<disableFusionUpdatesFromADManager>` můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí. V registru vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` v části `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1. Na příkazovém řádku nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat možnost přepsat nastavení fúze pomocí elementu `<disableFusionUpdatesFromADManager>`.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- [Schéma nastavení běhového prostředí](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
