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
ms.openlocfilehash: 7659dde4a2cb08fc3257d2f613ce4146522072b6
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706262"
---
# <a name="additional-class-libraries-and-apis"></a>Další knihovny tříd a rozhraní API

Rozhraní .NET Framework se neustále vyvíjí. Zlepšení vývoje napříč platformami a již v rané fázi zavedení nových funkcí, jsou vydávány nové funkce mimo pásmo (OOB). Toto téma obsahuje seznam projektů OOB, které zajišťuje dokumentaci.  
  
Kromě toho některé knihovny cílit na konkrétní platformy nebo implementace rozhraní .NET Framework. Například <xref:System.Text.CodePagesEncodingProvider> třídy zpřístupní kódování znakových stránek aplikací pro UWP vyvinuté pomocí rozhraní .NET Framework. Toto téma obsahuje také tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Projekt | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Obsahuje kolekce, které jsou vlákna bezpečné a zaručené nikdy nezmění jejich obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužné rutiny zpráv pro <xref:System.Net.Http.HttpClient> podle WinHTTP rozhraní Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Poskytuje knihovnu vektorové typy, které můžete využít výhod SIMD hardwarové akcelerace.| 
| <xref:System.Threading.Tasks.Dataflow> | Knihovna TPL datového toku poskytuje součásti toku dat a pomáhá tak zvýšit odolnost aplikace pro práci s souběžnosti. |  

## <a name="platform-specific-libraries"></a>Knihovny pro konkrétní platformu
  
| Projekt | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozšiřuje <xref:System.Text.EncodingProvider> třídy pro zpřístupnění kódování znakových stránek pro aplikace, které cílí univerzální platformu Windows. |  
  
## <a name="private-apis"></a>Soukromé rozhraní API  

Tato rozhraní API podporují produktovou infrastrukturu a nejsou určené nebo podporované pro použití přímo v kódu.  
  
| Název rozhraní API |
| -------- |
| [Třída System.Net.Connection](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList pole](../../../docs/framework/additional-apis/m_writelist.md) |
| [Třída System.Net.ConnectionGroup](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList pole](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData Class](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest. \_CoreResponse pole](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest.\_HttpResponse Field](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [Třída System.Windows.Forms.Design.DataMemberFieldEditor](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [Třída System.Windows.Forms.Design.DataMemberListEditor](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Viz také:

[Rozhraní .NET Framework a nesvázaná vydání](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
