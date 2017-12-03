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
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
