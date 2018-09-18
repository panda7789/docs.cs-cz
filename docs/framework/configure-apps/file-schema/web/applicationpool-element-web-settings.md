---
title: '&lt;applicationPool&gt; – Element (nastavení webu)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1a129abca5888120d03c42689ac825d768733a9d
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970250"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; – Element (nastavení webu)
Určuje nastavení konfigurace, který ASP.NET používá ke správě celého procesu chování, když aplikaci ASP.NET běží v integrovaném režimu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější.  
  
> [!IMPORTANT]
>  Tento element a funkci podporuje fungovat, pouze pokud je hostitelem aplikace technologie ASP.NET [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze.  
  
 \<Konfigurace >  
\<System.Web > – Element (nastavení webu)  
\<applicationPool > – Element (nastavení webu)  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|Určuje, kolik souběžných požadavků ASP.NET umožňuje jeden procesor.|  
|`maxConcurrentThreadsPerCPU`|Určuje, kolik souběžných vláken může být spuštěn fond aplikací, pro každý procesor. To poskytuje alternativní způsob řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, které můžete použít jeden procesor a jsou k obsluze požadavků. Ve výchozím nastavení toto nastavení je 0, což znamená, že technologie ASP.NET neomezuje počet vláken, která je možné vytvořit jeden procesor, i když fondu vláken CLR také omezuje počet vláken, která je možné vytvořit.|  
|`requestQueueLimit`|Určuje maximální počet požadavků, které lze zařadit do fronty pro technologii ASP.NET v jediném procesu. Když dva nebo více aplikací ASP.NET spustit v jediného fondu aplikací, můžou toto nastavení je kumulativní sadu požadavky na všechny aplikace ve fondu aplikací.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Obsahuje informace o způsobu interakce ASP.NET s hostitelskou aplikací.|  
  
## <a name="remarks"></a>Poznámky  
 Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace elementu vám umožní nakonfigurovat jak ASP.NET spravuje vláken a fronty požadavků, když je aplikace hostovaná ve fondu aplikací služby IIS. Je-li spustit služby IIS 6 nebo spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] v klasickém režimu nebo v režimu ISAPI, tato nastavení jsou ignorovány.  
  
 `applicationPool` Nastavení platí pro všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework. Nastavení jsou obsaženy v souboru aspnet.config. Existuje verze tohoto souboru pro verze 2.0, 4.0 rozhraní .NET Framework. (Verze 3.0 a 3.5 rozhraní .NET Framework sdílet s verzí 2.0 Soubor aspnet.config.)  
  
> [!IMPORTANT]
>  Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete nakonfigurovat samostatný aspnet.config souboru pro každý fond aplikací. Díky tomu můžete přizpůsobit výkonu vláken pro každý fond aplikací.  
  
 Pro `maxConcurrentRequestsPerCPU` nastavení, ve výchozím nastavení "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] efektivně vypne omezování žádostí, který je řízen technologie ASP.NET, pokud máte ve skutečnosti 5000 nebo více požadavků na CPU. Ve výchozím nastavení závisí na modulu CLR-fondu vláken k automatické správě souběžnosti jeden procesor a místo toho. Aplikace, které usnadňují používání příliš často používá asynchronní zpracování požadavků, nebo jež mají velký počet požadavků dlouhotrvající blokován v síti vstupně-výstupních operací, bude využívat zvýšení výchozí limit v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Nastavení `maxConcurrentRequestsPerCPU` na nulovou vypne použití spravovaných vláken pro zpracování požadavků ASP.NET. Pokud je aplikace spuštěna ve fondu aplikací služby IIS, požadavky zůstat ve vlákně vstupně-výstupních operací služby IIS a proto se omezuje souběžnosti vláken nastavením služby IIS.  
  
 `requestQueueLimit` Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut [processModel](https://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, který je nastavení v souborech Web.config pro aplikace ASP.NET. Ale `requestQueueLimit` přepíše nastavení v souboru aspnet.config `requestQueueLimit` nastavení v souboru Web.config. Jinými slovy Pokud oba atributy jsou nastavené (ve výchozím nastavení, to je PRAVDA), `requestQueueLimit` přednost má nastavení v souboru aspnet.config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat chování v celém procesu ASP.NET v souboru aspnet.config za následujících okolností:  
  
-   Aplikace je hostována v [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] fondu aplikací.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] běží v integrovaném režimu.  
  
-   Aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.  
  
 Hodnoty v tomto příkladu jsou výchozí hodnoty.  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a>Informace o elementu  
  
|||  
|-|-|  
|Obor názvů||  
|Název schématu||  
|Soubor ověření||  
|Může být prázdné.||  
  
## <a name="see-also"></a>Viz také  
 [\<System.Web > – Element (nastavení webu)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
