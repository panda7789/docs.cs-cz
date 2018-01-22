---
title: "Asynchronní operace (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b79112878141fd791c2fba183d2d1fec9f1b7044
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="asynchronous-operations-wcf-data-services"></a>Asynchronní operace (služby WCF Data Services)
Webové aplikace musí zohlednit zhorší latenci mezi klientem a serverem než aplikace, které běží v interních sítích. Chcete-li optimalizovat výkon a uživatelské prostředí aplikace, doporučujeme používat asynchronní metody <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy při přístupu k [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] servery prostřednictvím webu.  
  
 I když [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] servery proces protokolu HTTP požaduje asynchronně, některé metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] knihovny klienta jsou synchronní a počkejte na dokončení celého požadavků a odpovědí exchange před pokračováním provádění. Asynchronní metody [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] knihovny klienta není počkejte na dokončení této výměny a umožnit vaší aplikace do té doby zachování reagující uživatelské rozhraní.  
  
 Asynchronní operace můžete provádět pomocí metod pár na <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy, které začínají *začít* a *End* v uvedeném pořadí. *Začít* metody registrace delegáta, který služba volání při dokončení operace. *End* metody by měla být volána v delegáta, který je pro zpracování zpětného volání z dokončena operace registrována. Při volání *End* metodu za účelem dokončení asynchronní operace, je nutné provést ze stejné <xref:System.Data.Services.Client.DataServiceQuery%601> nebo <xref:System.Data.Services.Client.DataServiceContext> instance, kterého má začít operace. Každý *začít* metoda trvá `state` parametr, který můžete předat objekt stav zpětného volání. Tento stav objektu se načítají z <xref:System.IAsyncResult> který se dodává s zpětného volání a slouží k volání odpovídající *End* metoda pro dokončení asynchronní operace. Například když zadáte <xref:System.Data.Services.Client.DataServiceQuery%601> instance jako `state` parametr při volání <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metody u instance, stejné <xref:System.Data.Services.Client.DataServiceQuery%601> instance je vrácený <xref:System.IAsyncResult>. Tuto instanci <xref:System.Data.Services.Client.DataServiceQuery%601> se pak použije k volání <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metoda dokončit operaci dotazu. Další informace najdete v tématu [postup: provedení asynchronní dotazy dat služby](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md).  
  
> [!NOTE]
>  Pouze asynchronní operace jsou podporovány knihovny klienta, které jsou k dispozici v rozhraní .NET Framework pro Silverlight. Další informace najdete v tématu [datové služby WCF (Silverlight)](http://go.microsoft.com/fwlink/?LinkID=143149).  
  
 Knihovny klienta rozhraní .NET Framework podporují následující asynchronní operace:  
  
|Operace|Metody|  
|---------------|-------------|  
|Provádění <xref:System.Data.Services.Client.DataServiceQuery%601>.|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|Spuštění dotazu z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|Spuštění dávky dotazu z <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|Načítání související entity do <xref:System.Data.Services.Client.DataServiceContext>.|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|Změny se ukládají do objektů v<xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>Dělení na vlákna důležité informace pro asynchronní operace  
 Vícevláknové aplikace, není nutně vyvolání delegáta, který je registrovaný jako zpětné volání pro asynchronní operaci ve stejném vlákně, který se používá k volání *začít* metodu, která vytvoří počáteční požadavek. V aplikaci, kde musí být volána zpětné volání na konkrétní vlákno, musí explicitně zařazování provádění *End* metodu, která zpracuje odpověď požadované vlákno. Například v aplikacích na základě Windows Presentation Foundation WPF a aplikace založená na technologii Silverlight, odpovědi musí být zařazené zpět do vlákna uživatelského rozhraní pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metodu <xref:System.Windows.Threading.Dispatcher> objektu. Další informace najdete v tématu [dotaz na službu Data (WCF Data Services nebo Silverlight)](http://msdn.microsoft.com/library/3a7cdc07-c37e-4da2-b98b-c3763fd0970b).  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
