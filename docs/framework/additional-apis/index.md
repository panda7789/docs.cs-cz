---
title: Další knihovny tříd a rozhraní API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053247"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

.NET Framework se neustále vyvíjí. Pro zlepšení vývoje pro různé platformy a zavedení nových funkcí v brzkém případě jsou nové funkce vydány mimo pásmo (OOB). Toto téma obsahuje seznam projektů OOB, pro které poskytujeme dokumentaci.  
  
Kromě toho některé knihovny cílí na konkrétní platformy nebo implementace .NET Framework. <xref:System.Text.CodePagesEncodingProvider> Třída například zpřístupňuje kódování znakové stránky aplikacím UWP vyvinutým pomocí .NET Framework. Toto téma obsahuje i tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekce, které jsou vláknem bezpečné a zaručují, aby nikdy neměnily obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužnou rutinu zpráv <xref:System.Net.Http.HttpClient> pro založenou na rozhraní WinHTTP systému Windows. |
| <xref:System.Numerics> | Poskytuje knihovnu vektorových typů, které mohou využívat hardwarové akcelerace založené na SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | Knihovna TPL Dataflow poskytuje součásti toku dat, které vám pomůžou zvýšit odolnost aplikací s podporou souběžného zpracování. |  

## <a name="platform-specific-libraries"></a>Knihovny pro konkrétní platformu
  
| Project | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider> Rozšiřuje třídu tak, aby byly k dispozici kódování znakové stránky aplikacím, které cílí na Univerzální platforma Windows. |  
  
## <a name="private-apis"></a>Privátní rozhraní API  

Tato rozhraní API podporují infrastrukturu produktů a nejsou zamýšlená ani podporovaná pro použití přímo v kódu.  
  
| Název rozhraní API |
| -------- |
| [System .NET. Connection – třída](connection.md) |
| [System .NET. Connection. m\_WriteList – pole](m_writelist.md) |
| [System .NET. Connection – třída](connectiongroup.md) |
| [Pole System .NET. Connection. m\_ConnectionList](m_connectionlist.md) |
| [System.Net.CoreResponseData Class](coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](_autoredirects.md) |
| [System .NET. HttpWebRequest. \_Pole CoreResponse](httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest.\_HttpResponse Field](_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Viz také:

- [Rozhraní .NET Framework a nesvázaná vydání](../get-started/the-net-framework-and-out-of-band-releases.md)
