---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 193b783e44fe4386d3575e180dc5baa6a7f9a8be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Tento element může být pouze existuje-li `mode` atribut `<cookieHandler>` element je "Výchozí" nebo "Blokové".  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<cookieHandler >  
\<chunkedCookieHandler >  
  
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
|chunkSize|Maximální velikost ve znacích dat souboru cookie HTTP pro všechny jednoho souboru cookie HTTP. Musíte být opatrní při úpravě velikost bloku. Webových prohlížečů mají různé limity velikosti souborů cookie a počet povolený v každé doméně. Například specifikace původní Netscape stanoveno, tato omezení: celkový 300 soubory cookie, 4096 bajtů za hlavička cookie (včetně metadata, ne jenom hodnoty souboru cookie) a 20 souborů cookie na jednu doménu. Výchozí hodnota je 2000. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atribut `<cookieHandler>` element "Výchozí" nebo "Chunked", můžete zadat velikost bloku, který obslužná rutina souboru cookie používá číst a zapisovat soubory cookie zahrnutím `<chunkedCookieHandler>` podřízený element a nastavení jeho `chunkSize` atribut. Pokud `<chunkedCookieHandler>` element není k dispozici, je použita výchozí velikost bloku 2000 bajtů. Tento element nemůže být zadán, kdy `mode` je nastavena na hodnotu "Vlastní".  
  
 `<chunkedCookieHandler>` Element je reprezentována <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad konfiguruje soubor cookie rozdělený obslužná rutina, která soubory cookie se zapisují bloky 3000 bajtů.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
