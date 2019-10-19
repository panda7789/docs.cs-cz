---
title: Další knihovny tříd a rozhraní API
ms.date: 10/17/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 809ac026244b24aee69ec0d6c40c10a1248c234c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579118"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

.NET Framework se neustále vyvíjí. Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě jsou nové funkce vydány mimo pásmo (OOB). Toto téma obsahuje seznam projektů OOB, pro které poskytujeme dokumentaci.  
  
Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace .NET Framework. Například třída <xref:System.Text.CodePagesEncodingProvider> zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework. Toto téma obsahuje i tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužnou rutinu zpráv pro <xref:System.Net.Http.HttpClient> na základě rozhraní WinHTTP Windows. |
| <xref:System.Numerics> | Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. |  

## <a name="platform-specific-libraries"></a>Knihovny specifické pro platformu
  
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
* [System .NET. Connection – třída](connection.md)
* [System .NET. Connection. m \_WriteList pole](m_writelist.md)
* [System .NET. Connection – třída](connectiongroup.md)
* [System .NET. Connection. m \_ConnectionList pole](m_connectionlist.md)
* [System .NET. CoreResponseData – třída](coreresponsedata.md)
* [System .NET. CoreResponseData. m \_ResponseHeaders pole](coreresponsedata_m_responseheaders.md)
* [System .NET. CoreResponseData. m \_StatusCode pole](coreresponsedata_m_statuscode.md)
* [System .NET. HttpWebRequest. \_AutoRedirects – pole](_autoredirects.md)
* [System .NET. HttpWebRequest. \_CoreResponse – pole](httpwebrequest__coreresponse.md)
* [System .NET. HttpWebRequest. \_HttpResponse – pole](_httpresponse.md)
* [System .NET. ServicePoint. m \_ConnectionGroupList pole](m_connectiongrouplist.md)
* [System .NET. Třída ServicePointManager. s \_ServicePointTable pole](s_servicepointtable.md)
* [@No__t_1isDebuggerCheckDisabledForTestPurposes pole System. Windows. Diagnostics. VisualDiagnostics. s](s-isdebuggercheckdisabledfortestpurposes-field.md)
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
  
## <a name="see-also"></a>Viz také:

* [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
