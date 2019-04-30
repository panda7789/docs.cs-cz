---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795470"
---
# <a name="ws-metadataexchange-bindings"></a>WS-MetadataExchange Bindings
Toto téma popisuje, jak jsou vytvořeny výchozím vazbám metadata exchange pro různé přenosy.  
  
## <a name="the-default-bindings"></a>Výchozí vazby  
  
|Výchozí název vazby|Jak vytvořit vazbu|  
|--------------------------|------------------------------------|  
|mexHttpBinding|A <xref:System.ServiceModel.WSHttpBinding> se zabezpečením na úrovni přenosu zakázán.|  
|mexHttpsBinding|A <xref:System.ServiceModel.WSHttpBinding> , který podporuje zabezpečení na úrovni přenosu.|  
|mexNamedPipeBinding|A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.|  
|mexTcpBinding|A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.|
