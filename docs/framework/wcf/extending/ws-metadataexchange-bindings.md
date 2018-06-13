---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488621"
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
