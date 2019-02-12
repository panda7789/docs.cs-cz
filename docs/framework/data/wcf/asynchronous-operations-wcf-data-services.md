---
title: Asynchronní operace (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 1aa51d07be6073a75ef40ade83eba13371db3a69
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56094149"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Asynchronní operace (WCF Data Services)
Webové aplikace musí zohlednit vyšší latence mezi klientem a serverem než aplikace, které běží uvnitř interní sítě. Pokud chcete optimalizovat výkon a uživatelské prostředí aplikace, doporučujeme používat asynchronní metody <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy při přístupu k [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] servery prostřednictvím webu.  
  
 I když [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] servery proces protokolu HTTP požaduje asynchronně, některé metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny jsou synchronní a počkejte na dokončení výměně celý požadavků a odpovědí před pokračováním provádění. Asynchronní metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny nechcete čekat na dokončení této výměny a umožňuje vaší aplikaci k udržovat responzivní uživatelské rozhraní do té doby.  
  
 Asynchronní operace lze provádět pomocí dvojice metody <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy, které začínají *začít* a *End* v uvedeném pořadí. *Začít* zaregistrovat metody delegáta, který služba volání při dokončení operace. *End* metody by měla být volána v delegáta, který je registrován pro obsluhu zpětného volání z dokončené operace. Při volání *End* metoda k dokončení asynchronní operace, musíte to udělat z dané <xref:System.Data.Services.Client.DataServiceQuery%601> nebo <xref:System.Data.Services.Client.DataServiceContext> instanci, která jste použili k zahájení operace. Každý *začít* přijímá metodu `state` parametr, který můžete předat objektu stavu zpětného volání. Tento objekt stavu je načten z <xref:System.IAsyncResult> , který je součástí zpětné volání a slouží k volání odpovídající *End* metody pro dokončení asynchronní operace. Například když zadáte <xref:System.Data.Services.Client.DataServiceQuery%601> instance `state` parametru při volání <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metodu instance, stejné <xref:System.Data.Services.Client.DataServiceQuery%601> instance je vrácený <xref:System.IAsyncResult>. Tato instance <xref:System.Data.Services.Client.DataServiceQuery%601> se pak použije k volání <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda dokončit operaci dotazu. Další informace najdete v tématu [jak: Provádění dotazů v asynchronní datové služby](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Tyto klientské knihovny, které jsou k dispozici v rozhraní .NET Framework pro Silverlight podporuje pouze asynchronní operace. Další informace najdete v tématu [služeb WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Tyto klientské knihovny rozhraní .NET Framework podporuje následující asynchronní operace:  
  
|Operace|Metody|  
|---------------|-------------|  
|Provádění <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Provádění dotazu z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Provádění dotazu batch z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Načítají se související entitou do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Ukládají se změny objektů v <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Důležité informace pro asynchronní operace dělení na vlákna  
 Vícevláknové aplikace, není nutně vyvolán delegát, který je registrovaný jako zpětné volání pro asynchronní operaci ve stejném vlákně, která byla použita k volání *začít* metodu, která vytvoří počáteční požadavek. V aplikaci, ve kterém musí být zpětné volání vyvolat na konkrétním vlákně, musí explicitně zařazování provádění *End* metodu, která zpracuje odpověď do požadovaného vlákna. Například aplikace pro systém Windows Presentation Foundation WPF a aplikací založených na technologii Silverlight, odpověď musí zařadit zpět do vlákna uživatelského rozhraní pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metodu <xref:System.Windows.Threading.Dispatcher> objektu. Další informace najdete v tématu [dotazování v datové službě (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Viz také:
- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
