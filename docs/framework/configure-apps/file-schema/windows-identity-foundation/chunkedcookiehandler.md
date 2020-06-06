---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252110"
---
# \<chunkedCookieHandler>
Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler> . Tento element může být k dispozici pouze v případě, že `mode` atribut `<cookieHandler>` elementu je "výchozí" nebo "v bloku".  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Mění|Maximální velikost dat souborů cookie protokolu HTTP v znacích pro libovolný soubor cookie HTTP. Při upravování velikosti bloku dat musíte být opatrní. Webové prohlížeče mají různá omezení velikosti souborů cookie a počtu povolených v každé doméně. Původní specifikace aplikace Netscape například stanovila tyto limity: 300 souborů cookie celkem, 4096 bajtů na hlavičku souboru cookie (včetně metadat, nikoli jenom hodnota souboru cookie) a 20 souborů cookie na doménu. Výchozí hodnota je 2000. Povinná hodnota.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> jak bude (SAM) používat ke čtení a zápisu souborů cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud určíte <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atributu `<cookieHandler>` pro element na "výchozí" nebo "bloků", můžete určit velikost bloku dat, kterou obslužná rutina souborů cookie používá ke čtení a zápisu souborů cookie, a to zahrnutím `<chunkedCookieHandler>` podřízeného prvku a nastavením jeho `chunkSize` atributu. Pokud `<chunkedCookieHandler>` element není přítomen, je použita výchozí velikost bloku 2000 bajtů. Tento element nejde zadat, pokud `mode` je atribut nastavený na Custom (vlastní).  
  
 `<chunkedCookieHandler>`Element je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídou.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu se konfiguruje obslužná rutina souborů cookie s proměnlivým blokem, která zapisuje soubory cookie v blocích po 3000 bajtech.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
