---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117447"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>Element \<disableFusionUpdatesFromADManager>
Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|enabled|Požadovaný atribut.<br /><br /> Určuje, jestli je zakázaná výchozí možnost přepsat nastavení fúze.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Description|  
|-----------|-----------------|  
|0|Nepovolujte možnost přepsat nastavení fúze. Toto je výchozí chování, počínaje .NET Framework 4.|  
|1|Zakáže možnost přepsat nastavení fúze. Tím se vrátí chování dřívějších verzí .NET Framework.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 je výchozím chováním umožnit <xref:System.AppDomainManager> objektu přepsat konfigurační nastavení pomocí <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody, v podtřídě třídy <xref:System.AppDomainManager> . U výchozí domény aplikace nastavení, které změníte, přepíše nastavení, která byla určena konfiguračním souborem aplikace. Pro jiné aplikační domény přepíše nastavení konfigurace, která byla předána <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metodě nebo.  
  
 Můžete buď předat nové konfigurační informace, nebo předat hodnotu null ( `Nothing` v Visual Basic), aby se vyloučily informace o konfiguraci, které byly předány.  
  
 Nedávejte informace o konfiguraci do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti i do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody. Pokud předáte informace o konfiguraci do obou, informace, které předáte do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti, budou ignorovány, protože <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metoda přepisuje informace o konfiguraci z konfiguračního souboru aplikace. Použijete-li <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnost, můžete metodě předat hodnotu null ( `Nothing` v Visual Basic), <xref:System.AppDomainSetup.SetConfigurationBytes%2A> aby se vyloučily všechny konfigurační bajty, které byly zadány ve volání <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody nebo.  
  
 Kromě informací o konfiguraci můžete změnit následující nastavení <xref:System.AppDomainSetup> objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A> , <xref:System.AppDomainSetup.ApplicationName%2A> , <xref:System.AppDomainSetup.CachePath%2A> , <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> , <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A> , <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> , <xref:System.AppDomainSetup.DynamicBase%2A> , <xref:System.AppDomainSetup.LoaderOptimization%2A> , <xref:System.AppDomainSetup.PrivateBinPath%2A> , <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> , <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> a <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .  
  
 Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí. V registru vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework` a nastavte hodnotu na 1. Na příkazovém řádku nastavte proměnnou prostředí `COMPLUS_disableFusionUpdatesFromADManager` na 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat možnost přepsat nastavení fúze pomocí `<disableFusionUpdatesFromADManager>` elementu.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
- [Jak běhové prostředí vyhledává sestavení](../../../deployment/how-the-runtime-locates-assemblies.md)
