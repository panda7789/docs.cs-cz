---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152851"
---
# <a name="applicationpool-element-web-settings"></a>\<applicationPool> Element (Nastavení webu)
Určuje nastavení konfigurace, které ASP.NET používá ke správě chování celého procesu, když je aplikace ASP.NET spuštěna v integrovaném režimu ve službě IIS 7.0 nebo novější verzi.  
  
> [!IMPORTANT]
> Tento prvek a funkce, kterou podporuje, fungují pouze v případě, že je aplikace ASP.NET hostována ve službě IIS 7.0 nebo novějších verzích.  
  
[**\<>konfigurace**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<aplikacePool>**  
  
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
|`maxConcurrentRequestsPerCPU`|Určuje, kolik simultánních požadavků ASP.NET umožňuje na procesor.|  
|`maxConcurrentThreadsPerCPU`|Určuje, kolik simultánních podprocesů může být spuštěno pro fond aplikací pro každý procesor. To poskytuje alternativní způsob, jak řídit ASP.NET souběžnosti, protože můžete omezit počet spravovaných vláken, které lze použít na procesor k poskytování požadavků. Ve výchozím nastavení je toto nastavení 0, což znamená, že ASP.NET neomezuje počet podprocesů, které lze vytvořit na procesor, i když fond vláken CLR také omezuje počet podprocesů, které lze vytvořit.|  
|`requestQueueLimit`|Určuje maximální počet požadavků, které mohou být zařazeny do fronty pro ASP.NET v jednom procesu. Pokud jsou v jednom fondu aplikací spuštěny dvě nebo více ASP.NET aplikací, bude toto nastavení podléhat kumulativní sadě požadavků pro libovolnou aplikaci ve fondu aplikací.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|Obsahuje informace o tom, jak ASP.NET spolupracuje s hostitelskou aplikací.|  
  
## <a name="remarks"></a>Poznámky  

Při spuštění služby IIS 7.0 nebo novější verze v integrovaném režimu umožňuje tato kombinace prvků konfigurovat způsob správy ASP.NET požadavků vláken a front, když je aplikace hostována ve fondu aplikací služby IIS. Pokud spustíte službu IIS 6 nebo spustíte službu IIS 7.0 v klasickém režimu nebo v režimu ISAPI, budou tato nastavení ignorována.  
  
Nastavení `applicationPool` platí pro všechny fondy aplikací, které běží na konkrétní verzi rozhraní .NET Framework. Nastavení jsou obsažena v souboru aspnet.config. Existuje verze tohoto souboru pro verze 2.0 a 4.0 rozhraní .NET Framework. (Verze 3.0 a 3.5 rozhraní .NET Framework sdílejí soubor aspnet.config s verzí 2.0.)  
  
> [!IMPORTANT]
> Pokud v systému Windows 7 spustíte službu IIS 7.0, můžete nakonfigurovat samostatný soubor aspnet.config pro každý fond aplikací. To umožňuje přizpůsobit výkon podprocesů pro každý fond aplikací.  
  
Pro `maxConcurrentRequestsPerCPU` nastavení výchozí nastavení "5000" v rozhraní .NET Framework 4 efektivně vypne omezení požadavků, které je řízeno ASP.NET, pokud ve skutečnosti nemáte 5000 nebo více požadavků na procesor. Výchozí nastavení závisí místo toho na fondu vláken CLR, aby automaticky spravoval souběžnost na procesor. Aplikace, které rozsáhle využívají zpracování asynchronních požadavků nebo které mají mnoho dlouhotrvajících požadavků blokovaných v síťových vstupně-televizních službách, budou mít prospěch ze zvýšeného výchozího limitu v rozhraní .NET Framework 4. Nastavení `maxConcurrentRequestsPerCPU` na nulu vypne použití spravovaných podprocesů pro zpracování požadavků ASP.NET. Pokud je aplikace spuštěna ve fondu aplikací služby IIS, požadavky zůstávají ve vlákně iis V/O, a proto je souběžnost omezena nastavením podprocesu služby IIS.  
  
Nastavení `requestQueueLimit` funguje stejným způsobem `requestQueueLimit` jako atribut elementu [processModel,](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) který je nastaven v souborech Web.config pro ASP.NET aplikace. `requestQueueLimit` Nastavení v souboru aspnet.config však `requestQueueLimit` přepíše nastavení v souboru Web.config. Jinými slovy, pokud jsou nastaveny oba atributy (ve výchozím nastavení je to pravda), `requestQueueLimit` má přednost nastavení v souboru aspnet.config.  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování celého procesu v souboru aspnet.config za následujících okolností:  
  
- Aplikace je hostována ve fondu aplikací služby IIS 7.0.  
  
- Službu IIS 7.0 je spuštěna v integrovaném režimu.  
  
- Aplikace používá rozhraní .NET Framework 3.5 SP1 nebo novější verzi.  
  
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
|Ověřovací soubor||  
|Může být prázdný||  
  
## <a name="see-also"></a>Viz také

- [\<system.web> Element (Nastavení webu)](system-web-element-web-settings.md)
