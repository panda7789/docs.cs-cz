---
title: Asynchronní operace (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 01212b859e10ec1bbbb452486ce1aa6a2cecb583
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965818"
---
# <a name="asynchronous-operations-wcf-data-services"></a>Asynchronní operace (WCF Data Services)
Webové aplikace musí vyhovovat vysoké latenci mezi klientem a serverem než aplikace, které běží v interních sítích. Pro optimalizaci výkonu a uživatelského prostředí vaší aplikace doporučujeme použít asynchronní metody <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> při přístupu k [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] serverům přes web.  
  
 I když [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] servery zpracovávají požadavky HTTP asynchronně, některé metody klientských knihoven jsou synchronní a před pokračováním v provádění čekají na dokončení celého Exchange Request-Response. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Asynchronní metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientských knihoven nečekají na dokončení tohoto systému Exchange a mohou vaší aplikaci povolit, aby mezitím udržovala odpovídající uživatelské rozhraní.  
  
 Asynchronní operace lze provádět pomocí páru metod <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> , které začínají na *začátku* a na *konci* . Metody *Begin* zaregistrují delegáta, který služba volá po dokončení operace. *Koncové* metody by měly být volány v delegátovi, který je zaregistrován pro zpracování zpětného volání z dokončených operací. Při volání metody *End* k dokončení asynchronní operace je nutné provést operaci ze stejné <xref:System.Data.Services.Client.DataServiceQuery%601> nebo <xref:System.Data.Services.Client.DataServiceContext> instance, kterou jste použili k zahájení operace. Každá metoda *Begin* přebírá `state` parametr, který může předat objektu stavu zpětnému volání. Tento objekt stavu je načten z rozhraní <xref:System.IAsyncResult> , které je dodáváno se zpětným voláním a slouží k volání odpovídající metody *End* k dokončení asynchronní operace. Například <xref:System.Data.Services.Client.DataServiceQuery%601> při zadání instance <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> `state` jako parametru při volání metody na instanci je stejná <xref:System.Data.Services.Client.DataServiceQuery%601> instance vrácena pomocí <xref:System.IAsyncResult>. Tato instance <xref:System.Data.Services.Client.DataServiceQuery%601> je pak použita k <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> volání metody k dokončení operace dotazu. Další informace najdete v tématu [jak: Spouštění dotazů](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)na asynchronní datové služby  
  
> [!NOTE]
> Klientské knihovny, které jsou k dispozici v .NET Framework pro Silverlight, podporují pouze asynchronní operace. Další informace najdete v tématu [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Klientské knihovny .NET Framework podporují následující asynchronní operace:  
  
|Operace|Metody|  
|---------------|-------------|  
|Spouští se <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Spouští se dotaz z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Provádění dávkového dotazu z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Načítají se související entita do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Uložení změn objektů v<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Požadavky na dělení na vlákna pro asynchronní operace  
 V aplikaci s více vlákny není delegát, který je zaregistrován jako zpětné volání pro asynchronní operaci, nutně vyvolán ve stejném vlákně, které bylo použito pro volání metody *Begin* , která vytváří počáteční požadavek. V aplikaci, kde musí být zpětné volání vyvoláno v konkrétním vlákně, je nutné explicitně zařadit provedení metody *End* , která zpracovává odpověď, do požadovaného vlákna. Například v aplikacích založených na Windows Presentation Foundation (WPF) a aplikacích založených na programu Silverlight musí být odpověď zařazena zpět do vlákna uživatelského rozhraní pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody <xref:System.Windows.Threading.Dispatcher> objektu. Další informace najdete v tématu [dotazování datové služby (WCF Data Services/Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95)).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
