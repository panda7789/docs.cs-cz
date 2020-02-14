---
title: Další knihovny tříd a rozhraní API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 3a5134aa4407598e223fd2c938bfaac02cf9178c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215540"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

.NET Framework se neustále vyvíjí. Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě jsou nové funkce vydány mimo pásmo (OOB). Toto téma obsahuje seznam projektů OOB, pro které poskytujeme dokumentaci.  
  
Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace .NET Framework. Například třída <xref:System.Text.CodePagesEncodingProvider> zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework. Toto téma obsahuje i tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje popisovač zprávy pro <xref:System.Net.Http.HttpClient> v závislosti na rozhraní WinHTTP systému Windows. |
| <xref:System.Numerics> | Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. |  

## <a name="platform-specific-libraries"></a>Knihovny pro konkrétní platformu
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozšiřuje třídu <xref:System.Text.EncodingProvider> a zpřístupňuje kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows. |  
  
## <a name="private-apis"></a>Privátní rozhraní API  

Tato rozhraní API podporují infrastrukturu produktů a nejsou zamýšlená ani podporovaná pro použití přímo v kódu.  
  
* [Vlastnost Microsoft. SqlServer. Server. SmiOrderProperty. Item](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System. Exception. PrepForRemoting – metoda](system.exception.prepforremoting.md)
* [System. data. SqlTypes. SqlChars. Stream – vlastnost](system.data.sqltypes.sqlchars.stream.md)
* [System. data. SqlTypes. SqlStreamChars – konstruktor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System. data. SqlTypes. SqlStreamChars. CanSeek – vlastnost](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System. data. SqlTypes. SqlStreamChars. IsNull – vlastnost](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System. data. SqlTypes. SqlStreamChars. Length – vlastnost](system.data.sqltypes.sqlstreamchars.length.md)
* [System. data. SqlTypes. SqlStreamChars. Close – metoda](system.data.sqltypes.sqlstreamchars.close.md)
* [System. data. SqlTypes. SqlStreamChars. Dispose – metoda](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System. data. SqlTypes. SqlStreamChars. Flush – metoda](system.data.sqltypes.sqlstreamchars.flush.md)
* [System. data. SqlTypes. SqlStreamChars. Read – metoda](system.data.sqltypes.sqlstreamchars.read.md)
* [System. data. SqlTypes. SqlStreamChars. Seek – Metoda](system.data.sqltypes.sqlstreamchars.seek.md)
* [System. data. SqlTypes. SqlStreamChars. SetLength – metoda](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System. data. SqlTypes. SqlStreamChars. Write – Metoda](system.data.sqltypes.sqlstreamchars.write.md)
* [System. IO. typu MemoryStream není. InternalGetOriginAndLength – metoda](system.io.memorystream.internalgetoriginandlength.md)
* [System .NET. Connection – třída](connection.md)
* [System .NET. Connection. m\_pole WriteList](m_writelist.md)
* [System .NET. Connection – třída](connectiongroup.md)
* [System .NET. Connection. m\_pole ConnectionList](m_connectionlist.md)
* [System .NET. ConnectStream. Connection – vlastnost](system.net.connectstream.connection.md)
* [System .NET. CoreResponseData – třída](coreresponsedata.md)
* [System .NET. CoreResponseData. m\_pole ResponseHeaders hostitele](coreresponsedata_m_responseheaders.md)
* [System .NET. CoreResponseData. m\_pole StatusCode](coreresponsedata_m_statuscode.md)
* [Pole autoredirect pro System .NET. HttpWebRequest.\_](_autoredirects.md)
* [Pole System .NET. HttpWebRequest.\_CoreResponse](httpwebrequest__coreresponse.md)
* [Pole System .NET. HttpWebRequest.\_HttpResponse](_httpresponse.md)
* [System .NET. PooledStream. NetworkStream – vlastnost](system.net.pooledstream.networkstream.md)
* [System .NET. RtcState – třída](system.net.rtcstate.md)
* [System .NET. ServicePoint. m\_pole ConnectionGroupList](m_connectiongrouplist.md)
* [System .NET. Třída ServicePointManager. s\_pole ServicePointTable](s_servicepointtable.md)
* [System .NET. TlsStream. m_Worker – pole](system.net.tlsstream.m_worker.md)
* [System .NET. Security. SslState. SslProtocol – vlastnost](system.net.security.sslstate.sslprotocol.md)
* [System. ServiceModel. Channels. Message. BodyToString – metoda](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. Message. WriteStartHeaders – metoda](system.servicemodel.channels.message.writestartheaders.md)
* [System. Windows. Diagnostics. VisualDiagnostics. s\_pole isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor – třída](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. DataMemberListEditor – třída](datamemberlisteditor-class.md)
* [System. XML. XmlReader. CreateSqlReader – metoda](system.xml.xmlreader.createsqlreader.md)
* [ADODB. Rozhraní připojení](adodb.connection.md)
* [ADODB. Výčet EventReason](adodb.eventreasonenum.md)
* [ADODB. Výčet EventStatus](adodb.eventstatusenum.md)
* [stdole. Struktura DISPPARAMS](stdole.dispparams.md)
* [stdole. Struktura EXCEPINFO](stdole.excepinfo.md)
* [stdole. Vlastnost IFont.Name](stdole.ifont.name.md)
* [stdole. Rozhraní IFontDisp](stdole.ifontdisp.md)
* [stdole. IPicture. Handle – vlastnost](stdole.ipicture.handle.md)
* [stdole. IPictureDisp. Handle – vlastnost](stdole.ipicturedisp.handle.md)
* [stdole. Rozhraní StdFont](stdole.stdfont.md)
* [stdole. Rozhraní StdPicture](stdole.stdpicture.md)
  
## <a name="see-also"></a>Viz také

* [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
