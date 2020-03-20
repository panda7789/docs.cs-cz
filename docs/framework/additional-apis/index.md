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
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155905"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

Rozhraní .NET Framework se neustále vyvíjí. Chcete-li zlepšit vývoj napříč platformami a zavést nové funkce brzy, nové funkce jsou uvolněny mimo pásmo (OOB). Toto téma uvádí projekty OOB, pro které poskytujeme dokumentaci.  
  
Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace rozhraní .NET Framework. <xref:System.Text.CodePagesEncodingProvider> Například třída zpřístupňuje kódování znakové stránky pro aplikace UPW vyvinuté pomocí rozhraní .NET Framework. Toto téma obsahuje také tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekce, které jsou bezpečné pro přístup z více vláken a zaručeně nikdy nezmění jejich obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužnou rutinu zprávy založenou <xref:System.Net.Http.HttpClient> na rozhraní WinHTTP systému Windows. |
| <xref:System.Numerics> | Poskytuje knihovnu vektorových typů, které mohou využívat hardwarovou akceleraci SIMD.|
| <xref:System.Threading.Tasks.Dataflow> | Knihovna Toku dat TPL poskytuje komponenty toku dat, které pomáhají zvýšit robustnost aplikací s podporou souběžnosti. |  

## <a name="platform-specific-libraries"></a>Knihovny specifické pro platformu
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozšiřuje třídu <xref:System.Text.EncodingProvider> tak, aby kódovací stránky byly dostupné pro aplikace, které cílí na univerzální platformu Windows. |  
  
## <a name="private-apis"></a>Privátní api  

Tato řešení API podporují infrastrukturu produktů a nejsou určena nebo podporována pro použití přímo z vašeho kódu.  
  
* [Vlastnost Microsoft.SqlServer.Server.SmiOrderProperty.Item](microsoft.sqlserver.server.smiorderproperty.item.md)
* [Metoda System.Exception.PrepForRemoting](system.exception.prepforremoting.md)
* [Vlastnost System.Data.SqlTypes.SqlChars.Stream](system.data.sqltypes.sqlchars.stream.md)
* [Konstruktor System.Data.SqlTypes.SqlStreamChars](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [Vlastnost System.Data.SqlTypes.SqlStreamChars.CanSeek](system.data.sqltypes.sqlstreamchars.canseek.md)
* [Vlastnost System.Data.SqlTypes.SqlStreamChars.IsNull](system.data.sqltypes.sqlstreamchars.isnull.md)
* [Vlastnost System.Data.SqlTypes.SqlStreamChars.Length](system.data.sqltypes.sqlstreamchars.length.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Close](system.data.sqltypes.sqlstreamchars.close.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Dispose](system.data.sqltypes.sqlstreamchars.dispose.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Flush](system.data.sqltypes.sqlstreamchars.flush.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Read](system.data.sqltypes.sqlstreamchars.read.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Seek](system.data.sqltypes.sqlstreamchars.seek.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.SetLength](system.data.sqltypes.sqlstreamchars.setlength.md)
* [Metoda System.Data.SqlTypes.SqlStreamChars.Write](system.data.sqltypes.sqlstreamchars.write.md)
* [System.io.memorystream.internalGetOriginAndLength Metoda](system.io.memorystream.internalgetoriginandlength.md)
* [Třída system.net.connection](connection.md)
* [Pole WriteList souboru\_System.Net.Connection.m](m_writelist.md)
* [Třída System.Net.ConnectionGroup](connectiongroup.md)
* [Pole System.Net.ConnectionGroup.m\_ConnectionList](m_connectionlist.md)
* [Vlastnost System.Net.ConnectStream.Connection](system.net.connectstream.connection.md)
* [Třída System.Net.CoreResponseData](coreresponsedata.md)
* [Pole Hlavičky odpovědí System.Net.CoreResponseData.m\_](coreresponsedata_m_responseheaders.md)
* [Pole StatusCode System.Net.CoreResponseData.m\_](coreresponsedata_m_statuscode.md)
* [Systém.Net.HttpWebRequest. \_Pole Automatické přesměrování](_autoredirects.md)
* [Systém.Net.HttpWebRequest. \_Pole CoreResponse](httpwebrequest__coreresponse.md)
* [Systém.Net.HttpWebRequest. \_Pole HttpResponse](_httpresponse.md)
* [Vlastnost System.Net.PooledStream.NetworkStream](system.net.pooledstream.networkstream.md)
* [Třída System.Net.RtcState](system.net.rtcstate.md)
* [Pole System.Net.ServicePoint.m\_ConnectionGroupList](m_connectiongrouplist.md)
* [Pole ServicePointTable systému.Net.ServicePointManager.s\_](s_servicepointtable.md)
* [Pole System.Net.TlsStream.m_Worker](system.net.tlsstream.m_worker.md)
* [Vlastnost System.Net.Security.SslState.SslProtocol](system.net.security.sslstate.sslprotocol.md)
* [Metoda System.ServiceModel.Channels.Message.bodytostring](system.servicemodel.channels.message.bodytostring.md)
* [Metoda System.ServiceModel.Channels.Message.WriteStartHeaders](system.servicemodel.channels.message.writestartheaders.md)
* [Pole System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md)
* [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md)
* [Metoda System.Xml.XmlReader.CreateSqlReader](system.xml.xmlreader.createsqlreader.md)
* [Adodb. Rozhraní připojení](adodb.connection.md)
* [Adodb. Výčt usoudit událost](adodb.eventreasonenum.md)
* [Adodb. Výčt u stavů událostí](adodb.eventstatusenum.md)
* [stdole. Struktura DISPPARAMS](stdole.dispparams.md)
* [stdole. Struktura EXCEPINFO](stdole.excepinfo.md)
* [stdole. vlastnost IFont.Name](stdole.ifont.name.md)
* [stdole. Rozhraní IFontDisp](stdole.ifontdisp.md)
* [stdole. Vlastnost IPicture.Handle](stdole.ipicture.handle.md)
* [stdole. Vlastnost IPictureDisp.Handle](stdole.ipicturedisp.handle.md)
* [stdole. Rozhraní StdFont](stdole.stdfont.md)
* [stdole. Rozhraní StdPicture](stdole.stdpicture.md)
  
## <a name="see-also"></a>Viz také

* [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
