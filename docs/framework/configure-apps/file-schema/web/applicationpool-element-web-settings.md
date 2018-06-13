---
title: '&lt;applicationPool&gt; – Element (webové nastavení)'
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a2eafc6b5ad1446fd07518f877a8ec001ad8dbd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757694"
---
# <a name="ltapplicationpoolgt-element-web-settings"></a>&lt;applicationPool&gt; – Element (webové nastavení)
Určuje nastavení konfigurace, které jsou používány ASP.NET ke správě procesy chování, když aplikace ASP.NET běží v integrovaném režimu [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější.  
  
> [!IMPORTANT]
>  Tento prvek a funkci podporuje funguje jenom v případě, že je vaše aplikace ASP.NET hostované na [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze.  
  
 \<Konfigurace >  
\<System.Web > elementu (webové nastavení)  
\<applicationPool > – Element (webové nastavení)  
  
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
|`maxConcurrentRequestsPerCPU`|Určuje, kolik souběžných požadavků ASP.NET umožňuje za využití procesoru.|  
|`maxConcurrentThreadsPerCPU`|Určuje, kolik souběžných vláken můžete používat pro fond aplikací pro každý procesor. To poskytuje alternativní způsob řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, které lze použít na procesoru k obsluze požadavků. Ve výchozím nastavení toto nastavení je 0, což znamená, že technologie ASP.NET neomezuje počet vláken, které lze vytvořit na procesor, i když fondu vláken CLR také omezuje počet vláken, které lze vytvořit.|  
|`requestQueueLimit`|Určuje maximální počet požadavků, které lze zařadit do fronty pro technologii ASP.NET v jediném procesu. Pokud dva nebo více aplikací ASP.NET spustit v jeden fond aplikací, podléhá úhrnnou sadu oprav požadavkům na všechny aplikace ve fondu aplikací, toto nastavení.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<system.web>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|Obsahuje informace o spolupráci ASP.NET s hostitelskou aplikaci.|  
  
## <a name="remarks"></a>Poznámky  
 Při spuštění [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] nebo novější verze v integrovaném režimu, tato kombinace element vám umožní nakonfigurovat jak ASP.NET spravuje vláken a fronty požadavků, když je aplikace hostované ve fondu aplikací služby IIS. Je-li spustit služby IIS 6 nebo ji spustit [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] v klasickém režimu nebo v režimu ISAPI, tato nastavení ignorují.  
  
 `applicationPool` Nastavení se vztahují na všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework. Nastavení jsou obsaženy v souboru Soubor aspnet.config. Je verze tohoto souboru pro verze 2.0 a rozhraní .NET Framework 4.0. (Verze 3.0 a rozhraní .NET Framework 3.5 sdílet s verze 2.0 Soubor aspnet.config.)  
  
> [!IMPORTANT]
>  Pokud spustíte [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete nakonfigurovat samostatný soubor aspnet.config soubor pro každý fond aplikací. Díky tomu můžete přizpůsobit výkon vláken pro každý fond aplikací.  
  
 Pro `maxConcurrentRequestsPerCPU` nastavení, výchozí nastavení "5 000" v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] omezení požadavků efektivně vypne řízené ASP.NET, pokud máte ve skutečnosti 5000 nebo další požadavky na procesor. Výchozí nastavení, místo toho závisí na CLR-fondu vláken automaticky spravovat souběžnosti za využití procesoru. Aplikace, které usnadňují rozsáhlé používání asynchronní zpracování požadavků nebo které mají mnoho požadavků dlouho běžící zablokovaných v síti vstupně-výstupních operací, bude využívat vyšší výchozí limit v [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]. Nastavení `maxConcurrentRequestsPerCPU` na nulové vypne používání spravovaných vláken pro zpracování požadavků ASP.NET. Když aplikace běží v fond aplikací služby IIS, požadavky Zůstaňte na vlákno vstupně-výstupních operací služby IIS a proto je omezené souběžnosti vláken nastavení služby IIS.  
  
 `requestQueueLimit` Nastavení funguje stejným způsobem jako `requestQueueLimit` atribut [processModel](http://msdn.microsoft.com/library/4b8fe20e-74c8-4566-b72c-ce5f83c8e32d) element, který je nastaven v souborech Web.config pro aplikace ASP.NET. Ale `requestQueueLimit` přepíše nastavení v souboru aspnet.config `requestQueueLimit` nastavení v souboru Web.config. Jinými slovy Pokud jsou oba atributy (ve výchozím nastavení, to je true), `requestQueueLimit` přednost má nastavení v souboru Soubor aspnet.config.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat chování procesy ASP.NET v souboru aspnet.config v následujících případech:  
  
-   Aplikace je hostován v [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] fond aplikací.  
  
-   [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] je spuštěna v integrovaném režimu.  
  
-   Aplikace používá [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] nebo novější.  
  
 Hodnoty v příkladu jsou výchozí hodnoty.  
  
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
|Ověření souboru||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také  
 [\<System.Web > elementu (webové nastavení)](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
