---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: f5592e0fd02d34b2882182196e0aa9425672a8fe
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838296"
---
# <a name="ltchunkedcookiehandlergt"></a>&lt;chunkedCookieHandler&gt;
Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>. Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Výchozí" nebo "Rozdělený do bloků dat".  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
\<z toho důvodu >  
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
|chunkSize|Maximální velikost ve znacích dat souboru cookie HTTP pro všechny jednoho souboru cookie HTTP. Musíte být opatrní při nastavování velikosti bloku. Webových prohlížečů mají různá omezení velikosti souborů cookie a počet povolený v každé doméně. Například původní Netscape specifikace, které stanovila tato omezení: celkem 300 soubory cookie, 4096 bajtů na hlavička cookie (včetně metadat, ne jenom hodnoty souboru cookie) a 20 souborů cookie na jednu doménu. Výchozí hodnota je 2000. Požadováno.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<z toho důvodu >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.|  
  
## <a name="remarks"></a>Poznámky  
 Při zadání <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atribut `<cookieHandler>` prvků "Výchozí" nebo "Bloku dat", můžete zadat velikost bloku dat, která soubor cookie obslužná rutina se používá ke čtení a zápis souborů cookie zahrnutím `<chunkedCookieHandler>` podřízený element a nastavení jeho `chunkSize` atribut. Pokud `<chunkedCookieHandler>` prvek není k dispozici, je použit výchozí velikost bloku 2 000 bajtů. Tento element nemůže být zadán při `mode` atribut je nastaven na "Vlastní".  
  
 `<chunkedCookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví bloku dat souboru cookie obslužnou rutinu, která zapisuje soubory cookie v blocích 3000 bajtů.  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
