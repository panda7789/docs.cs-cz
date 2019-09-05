---
title: Element <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b65711ad8c404d1c4f54a6197faf598e2215226f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252653"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager> Element
Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<disableFusionUpdatesFromADManager>**  
  
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
  
|Value|Popis|  
|-----------|-----------------|  
|0|Nepovolujte možnost přepsat nastavení fúze. Toto je výchozí chování, počínaje .NET Framework 4.|  
|1|Zakáže možnost přepsat nastavení fúze. Tím se vrátí chování dřívějších verzí .NET Framework.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 je <xref:System.AppDomainManager> výchozím chováním umožnit objektu přepsat konfigurační nastavení <xref:System.AppDomainSetup.ConfigurationFile%2A> pomocí vlastnosti <xref:System.AppDomainSetup> nebo <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody objektu, který je předán vaší implementaci. metody v podtřídu třídy <xref:System.AppDomainManager>. <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> U výchozí domény aplikace nastavení, které změníte, přepíše nastavení, která byla určena konfiguračním souborem aplikace. Pro jiné aplikační domény přepíše nastavení konfigurace, která byla předána <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> metodě nebo. <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>  
  
 Můžete buď předat nové konfigurační informace, nebo předat hodnotu null (`Nothing` v Visual Basic), aby se vyloučily informace o konfiguraci, které byly předány.  
  
 Nedávejte informace o konfiguraci do <xref:System.AppDomainSetup.ConfigurationFile%2A> vlastnosti i do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody. Pokud předáte informace o konfiguraci do obou, informace, které předáte <xref:System.AppDomainSetup.ConfigurationFile%2A> do vlastnosti, budou ignorovány <xref:System.AppDomainSetup.SetConfigurationBytes%2A> , protože metoda přepisuje informace o konfiguraci z konfiguračního souboru aplikace. Použijete <xref:System.AppDomainSetup.ConfigurationFile%2A> -li vlastnost, můžete <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metodě předat hodnotu null`Nothing` (v Visual Basic), aby se vyloučily všechny konfigurační bajty <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> , které byly zadány ve volání metody <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> nebo.  
  
 Kromě informací o konfiguraci můžete změnit <xref:System.AppDomainSetup> následující nastavení objektu, který je předán vaší implementaci <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A> ,<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, ,<xref:System.AppDomainSetup.LoaderOptimization%2A>, ,<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>,a. <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A>  
  
 Jako alternativu k použití `<disableFusionUpdatesFromADManager>` elementu můžete zakázat výchozí chování vytvořením nastavení registru nebo nastavením proměnné prostředí. V registru vytvořte hodnotu DWORD s názvem `COMPLUS_disableFusionUpdatesFromADManager` `HKCU\Software\Microsoft\.NETFramework` nebo `HKLM\Software\Microsoft\.NETFramework`a nastavte hodnotu na 1. Na příkazovém řádku nastavte proměnnou `COMPLUS_disableFusionUpdatesFromADManager` prostředí na 1.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zakázat možnost přepsat nastavení fúze pomocí `<disableFusionUpdatesFromADManager>` elementu.  
  
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
