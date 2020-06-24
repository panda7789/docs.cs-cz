---
title: Další knihovny tříd a rozhraní API
description: Prozkoumejte další knihovny tříd a rozhraní API v .NET, včetně projektů OOB (out-of-band), knihoven specifických pro platformu a privátních rozhraní API.
ms.date: 06/12/2020
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: 0b888d2f0e80685ba993682b2f3067cf8aee15bc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989741"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

Tento článek obsahuje seznam .NET Framework rozhraní API, které byly buď vydány mimo pásmo, cílí na konkrétní platformu, nebo jsou privátní nebo interní typy.

## <a name="oob-projects"></a>Projekty OOB

Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě některé .NET Framework funkce byly vydány mimo pásmo (OOB).

| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužnou rutinu zpráv pro <xref:System.Net.Http.HttpClient> založenou na rozhraní WinHTTP systému Windows. |
| <xref:System.Numerics> | Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.|
| <xref:System.Threading.Tasks.Dataflow> | Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. |  

## <a name="platform-specific-libraries"></a>Knihovny specifické pro platformu

Některé knihovny cílí na konkrétní platformy. <xref:System.Text.CodePagesEncodingProvider>Třída například zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework.
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozšiřuje <xref:System.Text.EncodingProvider> třídu tak, aby byly k dispozici kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows. |  
  
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
* [System .NET. ComNetOS – třída](system.net.comnetos.md)
* [System .NET. Connection – třída](connection.md)
* [System .NET. Connection. m \_ WriteList – pole](m_writelist.md)
* [System .NET. Connection – třída](connectiongroup.md)
* [Pole System .NET. Connection. m \_ ConnectionList](m_connectionlist.md)
* [System .NET. ConnectStream. Connection – vlastnost](system.net.connectstream.connection.md)
* [System .NET. CoreResponseData – třída](coreresponsedata.md)
* [Pole System .NET. CoreResponseData. m \_ ResponseHeaders hostitele](coreresponsedata_m_responseheaders.md)
* [System .NET. CoreResponseData. m \_ StatusCode – pole](coreresponsedata_m_statuscode.md)
* [System .NET. ExceptionHelper – třída](system.net.exceptionhelper.md)
* [System .NET. HttpStatusDescription – třída](system.net.httpstatusdescription.md)
* [System .NET. HttpWebRequest. \_ Pole autoredirect](_autoredirects.md)
* [System .NET. HttpWebRequest. \_ Pole CoreResponse](httpwebrequest__coreresponse.md)
* [System .NET. HttpWebRequest. \_ Pole HttpResponse](_httpresponse.md)
* [System .NET. Logging – třída](system.net.logging.md)
* [System .NET. mail. MailAddressParser – třída](system.net.mail.mailaddressparser.md)
* [System .NET. mail. QuotedPairReader – třída](system.net.mail.quotedpairreader.md)
* [System .NET. MIME. MailBnfHelper – třída](system.net.mime.mailbnfhelper.md)
* [System .NET. PooledStream. NetworkStream – vlastnost](system.net.pooledstream.networkstream.md)
* [System .NET. RtcState – třída](system.net.rtcstate.md)
* [System .NET. Security. SslState. SslProtocol – vlastnost](system.net.security.sslstate.sslprotocol.md)
* [Pole System .NET. ServicePoint. m \_ ConnectionGroupList](m_connectiongrouplist.md)
* [System .NET. Třída ServicePointManager. CloseConnectionGroups – metoda](system.net.servicepointmanager.closeconnectiongroups.md)
* [Pole System .NET. Třída ServicePointManager. s \_ ServicePointTable](s_servicepointtable.md)
* [System .NET. TlsStream. m_Worker – pole](system.net.tlsstream.m_worker.md)
* [System .NET. UnsafeNclNativeMethods – třída](system.net.unsafenclnativemethods.md)
* [System .NET. WebHeaderCollection. AddInternal – metoda](system.net.webheadercollection.addinternal.md)
* [System. ServiceModel. Channels. Message. BodyToString – metoda](system.servicemodel.channels.message.bodytostring.md)
* [System. ServiceModel. Channels. Message. WriteStartHeaders – metoda](system.servicemodel.channels.message.writestartheaders.md)
* [Pole System. Windows. Diagnostics. VisualDiagnostics. s \_ isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System. Windows. Forms. Design. DataMemberFieldEditor – třída](datamemberfieldeditor-class.md)
* [System. Windows. Forms. Design. DataMemberListEditor – třída](datamemberlisteditor-class.md)
* [System.Xml.XmlReader. CreateSqlReader – metoda](system.xml.xmlreader.createsqlreader.md)
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

* [.NET Framework a vzdálené verze](../get-started/the-net-framework-and-out-of-band-releases.md)
