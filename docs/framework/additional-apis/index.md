---
title: Rozhraní API a knihovny další – třída
ms.custom: ''
ms.date: 01/29/2018
ms.prod: .net-framework-oob
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: 12
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d9ceb1ad24d4ba87fab7713ba61fed91eef26c4d
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="additional-class-libraries-and-apis"></a>Rozhraní API a knihovny další – třída

Rozhraní .NET Framework je neustále vyvíjejí a za účelem zlepšení vývoj pro různé platformy nebo zavést nové funkce již v rané fázi pro naše zákazníky, vydáváme nové funkce vzdálenou správu (OOB). Toto téma obsahuje seznam projektů OOB, které poskytujeme dokumentaci.  
  
Kromě toho některé knihovny cíle specifické platformy nebo implementace rozhraní .NET Framework. Například <xref:System.Text.CodePagesEncodingProvider> třída provede kódování kódu stránky k dispozici pro aplikace UWP vyvinuté pomocí rozhraní .NET Framework. Toto téma obsahuje také tyto knihovny.  
  
## <a name="oob-projects"></a>Projekty OOB
  
| Projekt | Popis |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Poskytuje kolekcí, které jsou vlákno bezpečné a zaručenou nikdy změnit jejich obsah. |
| <xref:System.Net.Http.WinHttpHandler> | Poskytuje obslužné rutiny zpráv pro <xref:System.Net.Http.HttpClient> založené na rozhraní WinHTTP systému Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Poskytuje knihovnu vektoru typy, které můžete využít výhod SIMD hardwarové akcelerace.| 
| <xref:System.Threading.Tasks.Dataflow> | Knihovna toku dat TPL poskytuje součásti toku dat a pomáhá tak zvýšit robustnost aplikací s povolenými souběžnosti. |  

## <a name="platform-specific-libraries"></a>Specifické pro platformu knihovny
  
| Projekt | Popis |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Rozšiřuje <xref:System.Text.EncodingProvider> třídy pro zpřístupnění kódování stránky kód pro aplikace, které cílí na univerzální platformu Windows. |  
  
## <a name="private-apis"></a>Soukromé rozhraní API  

Tato rozhraní API podpory produktu infrastruktury a nejsou určené/podporované pro použití přímo z vašeho kódu.  
  
| Název rozhraní API |
| -------- |
| [System.Net.Connection Class](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList Field](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup Class](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList Field](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData Class](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode Field](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest.\_AutoRedirects Field](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest.\_CoreResponse Field](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest.\_HttpResponse Field](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Viz také

[Rozhraní .NET Framework a nesvázaná vydání](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
