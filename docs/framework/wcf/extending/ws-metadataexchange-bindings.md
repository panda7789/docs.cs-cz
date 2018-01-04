---
title: WS-MetadataExchange Bindings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d305f3bf34b3b14da566fa792552e24e695ef33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bindings
Toto téma popisuje, jak se vytvářejí výchozí metadata exchange vazby pro různé přenosy.  
  
## <a name="the-default-bindings"></a>Výchozí vazby  
  
|Výchozí název vazby|Jak je vytvořený vazby|  
|--------------------------|------------------------------------|  
|MexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> s zabezpečení na úrovni přenosu zakázána.|  
|MexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> podporující zabezpečení na úrovni přenosu.|  
|MexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.|  
|MexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.|
