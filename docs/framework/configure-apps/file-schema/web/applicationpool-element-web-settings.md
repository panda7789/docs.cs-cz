---
title: Element <applicationPool> (nastavení webu)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: c88f4e5407e550047eaf0f5c8d0d2924da611e93
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699227"
---
# <a name="applicationpool-element-web-settings"></a>@no__t – 0applicationPool > – element (nastavení webu)
Určuje nastavení konfigurace, které ASP.NET používá ke správě chování v rámci procesu, když je aplikace ASP.NET spuštěná v integrovaném režimu na IIS 7,0 nebo novější verzi.  
  
> [!IMPORTANT]
> Tento prvek a funkce, které podporuje, fungují pouze v případě, že je vaše aplikace ASP.NET hostována ve službě IIS 7,0 nebo novějších verzích.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. Web >** ](system-web-element-web-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<applicationPool >**  
  
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
|`maxConcurrentRequestsPerCPU`|Určuje, kolik souběžných požadavků ASP.NET povoluje jednotlivé PROCESORy.|  
|`maxConcurrentThreadsPerCPU`|Určuje, kolik souběžných vláken může být spuštěno pro fond aplikací pro každý procesor. To poskytuje alternativní způsob pro řízení souběžnosti ASP.NET, protože můžete omezit počet spravovaných vláken, která lze použít pro jednotlivé PROCESORy k obsluze požadavků. Ve výchozím nastavení je toto nastavení 0, což znamená, že ASP.NET neomezuje počet vláken, která lze vytvořit pro jednotlivé PROCESORy, i když fond vláken CLR také omezuje počet vláken, která lze vytvořit.|  
|`requestQueueLimit`|Určuje maximální počet požadavků, které mohou být zařazeny do fronty pro ASP.NET v jednom procesu. V případě, že dvě nebo více ASP.NETch aplikací běží v jednom fondu aplikací, toto nastavení se vztahuje na kumulativní sadu požadavků, které se přidávají do jakékoli aplikace ve fondu aplikací.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[@no__t -1System. Web >](system-web-element-web-settings.md)|Obsahuje informace o tom, jak ASP.NET komunikuje s hostitelskou aplikací.|  
  
## <a name="remarks"></a>Poznámky  

Pokud spustíte službu IIS 7,0 nebo novější verzi v integrovaném režimu, tato kombinace prvků vám umožní nakonfigurovat, jak ASP.NET spravuje vlákna a fronty, když je aplikace hostována ve fondu aplikací služby IIS. Pokud spouštíte IIS 6 nebo v klasickém režimu nebo v režimu ISAPI spouštíte IIS 7,0, tato nastavení se ignorují.  
  
Nastavení `applicationPool` platí pro všechny fondy aplikací, které běží na konkrétní verzi .NET Framework. Nastavení jsou obsažena v souboru ASPNET. config. Verze tohoto souboru je verze 2,0 a 4,0 .NET Framework. (Verze 3,0 a 3,5 .NET Framework sdílet soubor ASPNET. config s verzí 2,0.)  
  
> [!IMPORTANT]
> Spouštíte-li službu IIS 7,0 na [!INCLUDE[win7](../../../../../includes/win7-md.md)], můžete pro každý fond aplikací nakonfigurovat samostatný soubor ASPNET. config. To vám umožní přizpůsobit výkon vláken pro každý fond aplikací.  
  
U nastavení `maxConcurrentRequestsPerCPU` je ve výchozím nastavení "5000" v .NET Framework 4 účinně vypnuté omezení požadavků, které je řízeno ASP.NETou, pokud ve skutečnosti nemáte 5000 nebo více požadavků na procesor. Výchozí nastavení závisí na fondu vláken CLR k automatické správě souběžnosti na procesor. Aplikace, které vytvářejí rozsáhlé použití asynchronního zpracování požadavků nebo které mají v síťové vstupně-výstupní operaci blokované množství dlouhotrvajících požadavků, budou těžit z zvýšeného výchozího limitu .NET Framework 4. Nastavení `maxConcurrentRequestsPerCPU` na hodnotu nula vypne používání spravovaných vláken pro zpracování požadavků ASP.NET. Když je aplikace spuštěná ve fondu aplikací služby IIS, požadavky zůstanou ve vstupně-výstupních vláknech služby IIS a proto souběžnost je omezena nastavením vlákna IIS.  
  
Nastavení `requestQueueLimit` funguje stejným způsobem jako atribut `requestQueueLimit` prvku [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) , který je nastaven v souborech Web. config pro aplikace ASP.NET. Nastavení `requestQueueLimit` v souboru ASPNET. config však přepisuje nastavení `requestQueueLimit` v souboru Web. config. Jinými slovy, pokud jsou oba atributy nastaveny (ve výchozím nastavení je to pravda), má přednost nastavení `requestQueueLimit` v souboru ASPNET. config.  
  
## <a name="example"></a>Příklad  

Následující příklad ukazuje, jak nakonfigurovat ASP.NET chování v rámci procesu v souboru ASPNET. config v následujících případech:  
  
- Aplikace je hostována ve fondu aplikací služby IIS 7,0.  
  
- Služba IIS 7,0 je spuštěna v integrovaném režimu.  
  
- Aplikace používá .NET Framework 3,5 SP1 nebo novější verzi.  
  
Hodnoty v příkladu jsou výchozími hodnotami.  
  
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
|Může být prázdné||  
  
## <a name="see-also"></a>Viz také:

- [@no__t element -1System. Web > (nastavení webu)](system-web-element-web-settings.md)
